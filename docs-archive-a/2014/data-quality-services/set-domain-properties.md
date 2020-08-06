---
title: Establecer las propiedades del dominio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.domainproperties.f1
ms.assetid: 8a3c88ca-31d6-4f75-9aca-cf027c6d9845
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 328dc061f59739ea52f6b14513b970d97352abc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751506"
---
# <a name="set-domain-properties"></a>Establecer las propiedades de dominio
  En este tema se describe cómo establecer las propiedades del dominio en [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
 Para establecer las propiedades de un dominio, debe haber creado una base de conocimiento y un dominio.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Debe disponer del rol dqs_kb_editor o dqs_administrator en la base de datos DQS_MAIN para establecer las propiedades de un dominio.  
  
##  <a name="set-domain-properties"></a><a name="Set"></a>Establecer propiedades de dominio  
  
1.  Para establecer las propiedades de un dominio existente, abra una base de conocimiento en la actividad Administración de dominios (vea [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)) y seleccione el dominio adecuado en la lista **Dominio** . La página Propiedades del dominio se mostrará de forma predeterminada.  
  
2.  Para establecer las propiedades de un dominio nuevo después de crearlo, use el procedimiento que se describe en [Create a Domain](../../2014/data-quality-services/create-a-domain.md).  
  
3.  Haga clic en **Finalizar** para finalizar la actividad de administración de dominios, tal como se describe en [Finalizar la actividad Administración de dominios](../../2014/data-quality-services/end-the-domain-management-activity.md).  
  
##  <a name="follow-up-after-setting-domain-properties"></a><a name="FollowUp"></a>Seguimiento: después de establecer las propiedades de dominio  
 Una vez establecidas las propiedades del dominio, puede realizar en él otras tareas de administración, ejecutar la detección de conocimiento para agregar conocimiento al dominio o agregar a este una directiva de coincidencia. Para más información, vea [Realizar la detección de conocimiento](../../2014/data-quality-services/perform-knowledge-discovery.md), [Administrar un dominio](../../2014/data-quality-services/managing-a-domain.md) o [Crear una directiva de coincidencia](../../2014/data-quality-services/create-a-matching-policy.md).  
  
##  <a name="domain-properties"></a><a name="Properties"></a>Propiedades de dominio  
  
###  <a name="domain-name-and-description"></a><a name="Name"></a>Nombre de dominio y descripción  
 Una vez creado un dominio, no se puede cambiar ni su nombre ni su descripción. El nombre del dominio debe ser único para la base de conocimiento. La descripción puede contener un máximo de 256 caracteres.  
  
###  <a name="data-type"></a>Tipo de datos <a name="Type"></a>  
 Al crear el dominio, seleccione uno de los siguientes tipos de datos para los valores del dominio: **Cadena** (valor predeterminado), **Fecha**, **Entero**o **Decimal**. Después de crear el dominio, podrá ver el tipo de datos, pero no cambiarlo. El tipo de datos seleccionado para un dominio define el tipo de datos de origen que se puede asignar al dominio. Para más información sobre los tipos de datos admitidos para cada uno de los tipos de datos de dominio en DQS, vea [Compatibilidad con los tipos de datos en SQL Server y SSIS para dominios DQS](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).  
  
###  <a name="use-leading-values"></a><a name="Leading"></a>Usar valores iniciales  
 Seleccione esta casilla para especificar que se mostrará el valor inicial de un grupo de sinónimos en lugar de un valor que sea un sinónimo de aquel. Anule la selección **Usar valores iniciales** para especificar que cada valor de sinónimo se mostrará en su forma correcta o corregida, y que no será reemplazado por el valor inicial de su grupo.  
  
###  <a name="normalize-string"></a><a name="Normalize"></a>Normalizar cadena  
 Si el tipo de datos es **Cadena**, haga clic en los caracteres especiales en los datos de origen para el procesamiento de calidad de datos de DQS. DQS reemplaza internamente los caracteres especiales con un valor NULL o un espacio cuando se cargan los datos en el dominio. Los dos puntos, el guion, el punto, las comillas dobles y el punto y coma se reemplazan por un espacio. La comilla simple se reemplaza por un valor NULL. El uso de valores NULL provoca que las dos partes de la cadena se unan.  
  
 Si se omiten los caracteres especiales en un valor de cadena, se puede incrementar la precisión de las correspondencias. La puntuación de similitud entre dos cadenas se puede aumentar reemplazando los caracteres especiales por valores NULL o espacios. Es posible que los signos de puntuación y otros símbolos sean distintos en cadenas diferentes. Cuando se reemplazan los caracteres especiales internamente, la puntuación puede superar el umbral de coincidencia mínimo en DQS, lo que puede provocar que se consideren coincidentes dos cadenas que, en caso contrario, no se habrían considerado como tales. Sin embargo, la decisión de omitir los caracteres especiales puede depender del tipo de datos en los que esté realizando la búsqueda de coincidencias. Por ejemplo, cuando se trabaja con datos en el sistema anglosajón de unidades, la omisión de comillas dobles y comillas simples puede producir falsos positivos si una comilla doble representa una pulgada y una comilla simple representa un pie.  
  
 La normalización se realiza cuando se cargan y se indizan datos durante las fases del procesamiento de datos: actividades de detección, directiva de coincidencia, proyecto de búsqueda de coincidencias y proyecto de limpieza. Si está habilitada, la normalización y la transformación de relaciones basadas en términos se realizan en una fase previa al procesamiento, antes del análisis final. Se ejecutan en cada dominio antes de que se apliquen los algoritmos que calculan la similitud entre las cadenas. Si se solicita el análisis inicial de un dominio compuesto, este se realizará antes de la normalización y de la transformación de relaciones basadas en términos, ya que el análisis inicial de delimitadores requiere símbolos. Otras operaciones, como los cambios en las reglas y en los valores del dominio, se llevan a cabo después de las transformaciones. Los datos resultantes no cambian cuando se reemplazan internamente los caracteres especiales en DQS.  
  
###  <a name="format-output-to"></a><a name="Format"></a>Dar formato a la salida  
 Seleccione el formato que se aplicará cuando se generen los valores de los datos del dominio. El formato es específico del tipo de datos seleccionado, tal como se muestra en la lista siguiente. Seleccione **Ninguno** si no desea aplicar ninguno de los formatos de la lista.  
  
-   Para un valor de cadena, puede especificar que esta se genere en mayúsculas, en minúsculas o con la inicial en mayúsculas.  
  
-   Para un valor de fecha, puede especificar el formato del día, del mes y del año.  
  
-   Para un valor entero, puede especificar el tipo de máscara de formato que se aplicará.  
  
-   Para un valor decimal, puede especificar la precisión y el tipo de máscara de formato que se aplicará.  
  
###  <a name="language"></a><a name="Language"></a>Módulo  
 Si el tipo de datos es **Cadena**, seleccione el idioma que desea asociar al dominio para el corrector ortográfico. Esta selección solo afecta al corrector ortográfico, ya que los resultados de este dependen del idioma que se está usando. La selección solo se aplica a un dominio individual cuyo tipo de datos sea de cadena. La propiedad de idioma no es relevante en los dominios compuestos. El idioma de cada parte de un dominio compuesto lo determina el dominio individual correspondiente.  
  
 El idioma predeterminado es inglés. Cuando se establece la propiedad **Idioma** en **Otros** , se deshabilita el corrector ortográfico para el dominio.  
  
> [!TIP]  
>  Si el idioma no aparece en la lista desplegable **Idioma** , debe seleccionar **Otro**. Esto garantiza que DQS limpia y elimina los duplicados para los datos de idioma no enumerados en función del conocimiento disponibles (reglas de dominio, valores de dominio, TBR, regla de coincidencia) en el dominio.  
  
###  <a name="enable-speller"></a><a name="Speller"></a>Habilitar corrector ortográfico  
 Si el tipo de datos es **Cadena**, haga clic aquí para habilitar el corrector ortográfico de DQS en el dominio. El corrector ortográfico solo funciona en dominios cuyo tipo de datos es de cadena. La casilla **Habilitar corrector ortográfico** habilita el corrector ortográfico solo en el dominio individual que está asociado a la casilla. La casilla no se aplica a un dominio compuesto.  
  
 El corrector ortográfico propone correcciones de sintaxis y de validación para los valores del dominio. Para obtener más información, vea [Use the DQS Speller](../../2014/data-quality-services/use-the-dqs-speller.md).  
  
###  <a name="disable-syntax-error-algorithms"></a><a name="Syntax"></a>Deshabilitar algoritmos de error de sintaxis  
 Si el tipo de datos es **Cadena**, seleccione esta opción para que DQS no identifique los errores de sintaxis en el dominio durante el proceso de limpieza. Active esta casilla si la identificación de los errores de sintaxis en el dominio es irrelevante. Por ejemplo, la identificación de los errores de sintaxis puede no afectar a un número de serie. Este control solo está disponible para el tipo de datos de cadena. DQS no comprobará los errores de sintaxis en los tipos de datos que no son de cadena.  
  
  
