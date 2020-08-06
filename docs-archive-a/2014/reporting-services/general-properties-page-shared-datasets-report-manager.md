---
title: Página de propiedades generales, conjuntos de recursos compartidos (Administrador de informes) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10798e41-24c3-4e69-893b-7ee6af7fc958
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31825e61cb40505e9167cc2b930a5b79e5aaa013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678058"
---
# <a name="general-properties-page-shared-datasets-report-manager"></a>Página de propiedades generales, conjuntos de datos compartidos (Administrador de informes)
  Utilice la página Conjunto de datos compartido para ver y administrar las propiedades de un elemento de conjunto de datos compartido.  
  
 En el Administrador de informes no puede ver ni cambiar la definición del conjunto de datos compartido, incluida la consulta. Para cambiar la definición, debe utilizar una herramienta de creación para abrir y modificar la definición, y después guardarla en el servidor de informes.  
  
 Con un conjunto de datos compartido, puede administrar los valores para un conjunto de datos de forma independiente de los informes, componentes y otros elementos de catálogo que lo utilizan.  
  
## <a name="navigation"></a>Navegación  
 Utilice el procedimiento siguiente para navegar hasta esta ubicación en la interfaz de usuario (IU).  
  
###### <a name="to-open-the-shared-dataset-properties-page-for-a-shared-dataset"></a>Para abrir la página de propiedades de Conjunto de datos compartidos para un conjunto de datos compartido  
  
1.  Abra el Administrador de informes y busque el conjunto de datos compartido para el que desea configurar las propiedades.  
  
2.  Mantenga el mouse sobre el conjunto de datos compartido y haga clic en la flecha de lista desplegable.  
  
3.  En la lista desplegable, haga clic en **Administrar**. Se abre la página de propiedades General.  
  
## <a name="options"></a>Opciones  
 **Nombre**  
 Escriba un nombre para el conjunto de datos compartido, que se usa para identificar el elemento en la jerarquía de carpetas del servidor de informes.  
  
 **Descripción**  
 Proporcione información sobre el conjunto de datos compartido. Esta descripción aparecerá en la página Contenido.  
  
 **Ocultar en la vista de lista**  
 Oculte el conjunto de datos compartido de los usuarios que están utilizando el modo de vista de lista en el Administrador de informes. El modo de vista de lista es el formato de vista predeterminado al explorar la jerarquía de carpetas del servidor de informes. En la vista de lista, los nombres y descripciones de elementos se presentan en formato horizontal. El formato alternativo es la vista Detalles. La vista Detalles no incluye descripciones, pero sí otra información acerca del elemento. Aunque se puede ocultar un elemento en la vista de lista, no se puede ocultar en la vista Detalles. Si desea restringir el acceso a un elemento, deberá crear una asignación de roles.  
  
 **Tiempo de espera de ejecución de la consulta**  
 Escriba el número de segundos hasta que se agote el tiempo de espera de la consulta. Si es 0, no se agota el tiempo de espera de la consulta.  
  
 **Aplicar**  
 Guarde los cambios.  
  
 **Eliminar**  
 Quite el conjunto compartido de la base de datos del servidor de informes. Al eliminar un conjunto de datos compartido desactiva los informes o las versiones en memoria caché. Para reactivar un informe, debe abrir uno por uno en una herramienta de creación de informes y especificar un conjunto de datos con el mismo nombre y la misma colección de campos. O bien, puede actualizar cada referencia a la región de datos para utilizar un conjunto de datos diferente con la misma colección de campos.  
  
 **Mover**  
 Cambie la posición de un conjunto de datos compartido en la jerarquía de carpetas del servidor de informes. Si hace clic en este botón, se abre la página Mover elementos, en la que puede examinar las carpetas para buscar una nueva ubicación de carpeta. Para obtener más información, vea [Página de elementos de movimiento &#40;Administrador de informes&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Descargar**  
 Extraiga una copia de la definición del conjunto de datos compartido. En función de las asociaciones de archivos definidas en su equipo, el archivo se abrirá en Visual Studio o en otra aplicación. En la mayoría de los casos, el conjunto de datos compartido se abre como un archivo XML.  
  
 **Sustituya**  
 Reemplace la definición del conjunto de datos compartido por otra diferente de un archivo .rsd que se encuentra en el sistema de archivos.  
  
## <a name="see-also"></a>Consulte también  
 [Administrador de informes &#40;Modo nativo de SSRS&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Administrador de informes de &#40;de página de contenido&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Administrador de informes la ayuda F1](../../2014/reporting-services/report-manager-f1-help.md)   
 [Opciones de actualización de caché &#40;Administrador de informes&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md)   
 [Página de almacenamiento en caché, conjuntos de recursos compartidos &#40;Administrador de informes&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md)   
 [Administrar conjuntos de recursos compartidos](report-data/manage-shared-datasets.md)   
 [Almacenar en caché conjuntos de datos compartidos &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md)  
  
  
