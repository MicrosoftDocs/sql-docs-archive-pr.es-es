---
title: Definir cálculos de inteligencia de tiempo mediante el Asistente de Business Intelligence | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- period over period growth [Analysis Services]
- parallel period comparisons [Analysis Services]
- Business Intelligence enhancements [Analysis Services], time intelligence
- time views [Analysis Services]
- hierarchies [Analysis Services], time
- time periods [Analysis Services]
- moving averages
- time [Analysis Services]
- period to date [Analysis Services]
- calculations [Analysis Services], time
- time hierarchies [Analysis Services]
- time intelligence [Analysis Services]
ms.assetid: be36e8fc-f46e-4553-8623-b27d695c330b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 222efb572c227e6a8ca3d1e2295b662cb586184a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663768"
---
# <a name="define-time-intelligence-calculations-using-the-business-intelligence-wizard"></a>Definir cálculos de inteligencia de tiempo mediante el Asistente de Business Intelligence
  La mejora de inteligencia de tiempo es una mejora del cubo que agrega cálculos de tiempo (o vistas de tiempo) a una jerarquía seleccionada. Esta mejora admite las siguientes categorías de cálculos:  
  
-   Períodos hasta la fecha.  
  
-   Crecimiento entre períodos.  
  
-   Media móvil.  
  
-   Comparaciones de período paralelas.  
  
 Se aplica la inteligencia de tiempo a los cubos que tienen una dimensión de tiempo. (Una dimensión de tiempo es una dimensión cuya propiedad `Type` se establece como `Time`). Además, los atributos de tiempo de esa dimensión también deben tener la configuración apropiada (como Years o Months) para su propiedad `Type`. La propiedad `Type` de la dimensión y sus atributos se establece correctamente si se usa el Asistente para dimensiones para crear la dimensión de tiempo.  
  
 Para agregar inteligencia de tiempo a un cubo, se usa el Asistente de Business Intelligence y se selecciona la opción **Definir la inteligencia de tiempo** de la página **Elegir mejora** . Este asistente le guiará por el proceso para seleccionar una jerarquía a la que se agrega inteligencia de tiempo y especificar los miembros de la jerarquía a los que se aplicará inteligencia de tiempo. En la última página del asistente, puede ver los cambios que se realizarán en la base de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] datos para agregar la inteligencia de tiempo seleccionada.  
  
## <a name="selecting-a-time-hierarchy"></a>Seleccionar una jerarquía de tiempo  
 En la página **Elegir cálculos y jerarquía de destino** , seleccione la jerarquía de tiempo para la que se aplica la mejora de tiempo. Puede aplicar la mejora de tiempo a una sola jerarquía de tiempo cada vez que se ejecuta el Asistente de Business Intelligence. Si desea aplicar la mejora a más de una jerarquía de tiempo, se vuelve a ejecutar el asistente.  
  
 Después de seleccionar una jerarquía de tiempo, en la lista **Cálculos de tiempo disponibles** seleccione los cálculos que afectan a la jerarquía. Los cálculos enumerados dependen de los niveles de la jerarquía y de la configuración de la propiedad `Type` para el atributo para cada nivel. Por ejemplo, una jerarquía Años admite Valor anual hasta la fecha y Porcentaje de crecimiento de año a año, pero una jerarquía Trimestres no.  
  
> [!NOTE]  
>  El archivo de plantilla Timeintelligence.xml define los cálculos de tiempo que se enumeran en **Cálculos de tiempo disponibles**. Si los cálculos enumerados no cubren sus necesidades, puede cambiar los cálculos existentes o agregar nuevos cálculos al archivo Timeintelligence.xml.  
  
> [!TIP]  
>  Para ver una descripción de un cálculo, use las flechas arriba y abajo para resaltar el cálculo.  
  
## <a name="apply-time-views-to-members"></a>Aplicar vistas de tiempo a los miembros  
 En la página **Definir el ámbito de cálculo** , se especifican los miembros a los que se aplican las nuevas vistas de tiempo. Puede aplicar las nuevas vistas de tiempo a uno de los siguientes objetos:  
  
-   **Miembros de una dimensión de cuentas** En la página **Definir el ámbito de cálculo** , la lista **Medidas disponibles** incluye dimensiones de cuentas. Las dimensiones de cuentas tienen su propiedad `Type` configurada como `Accounts`. Si tiene una dimensión de cuentas pero esa dimensión no figura en la lista **Medidas disponibles** , puede usar el Asistente de Business Intelligence para aplicar la inteligencia de cuentas a esa dimensión. Para obtener más información, vea [Agregar inteligencia de cuentas a una dimensión](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
-   **Medidas** En lugar de especificar una dimensión de cuentas, puede especificar las medidas a las que se aplican las vistas de tiempo. En este caso, seleccione las vistas a las que se aplican los cálculos de tiempo seleccionados. Por ejemplo, los activos y pasivos son datos del año hasta la fecha, por lo tanto no se aplica un cálculo de Valor anual hasta la fecha a medidas de activos o pasivos.  
  
## <a name="viewing-the-time-intelligence-enhancement"></a>Ver la mejora de inteligencia de tiempo  
 En la última página del Asistente de Business Intelligence, puede ver los cambios que se realizarán en la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Para una mejora de inteligencia de tiempo, el asistente cambia la dimensión de tiempo seleccionada, la vista del origen de datos relacionada y el cubo asociado como se describe en la siguiente tabla.  
  
|Object|Cambio|  
|------------|------------|  
|Dimensión de tiempo|Agrega un atributo para cada cálculo (o vista).|  
|Vista del origen de datos|Agrega una columna calculada en la tabla de tiempo para cada nuevo atributo en la dimensión de tiempo.|  
|Cubo|Agrega un miembro calculado que define el código de Expresiones multidimensionales (MDX) para realizar el cálculo.|  
  
## <a name="see-also"></a>Consulte también  
 [Crear miembros calculados](create-calculated-members.md)  
  
  
