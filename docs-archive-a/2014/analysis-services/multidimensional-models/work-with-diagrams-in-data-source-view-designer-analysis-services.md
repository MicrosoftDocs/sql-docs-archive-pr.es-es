---
title: Trabajar con diagramas en el diseñador de vistas del origen de datos (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.diagramorganizerpane.f1
- sql12.asvs.dsvdesigner.findtable.f1
- sql12.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40a58ed33ff6cfaebf2a6e7c084500dd3ae072da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673341"
---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a>Trabajar con diagramas en el Diseñador de vistas del origen de datos (Analysis Services)
  Un diagrama de vista del origen de datos (DSV) es una representación visual de los objetos de una DSV. Puede trabajar con el diagrama de forma interactiva para agregar, ocultar, eliminar o modificar objetos específicos. También puede crear varios diagramas en la misma DSV para resaltar un subconjunto de los objetos.  
  
 Para cambiar el área del diagrama que se muestra en el panel de diagramas, haga clic en la flecha de cuatro puntas de la esquina inferior derecha del panel y, a continuación, arrastre el cuadro de selección sobre el diagrama en miniatura hasta seleccionar el área que desea que aparezca en el panel de diagramas.  
  
 Este tema incluye las siguientes secciones:  
  
 [Agregar un diagrama](#bkmk_add)  
  
 [Modificar o eliminar un diagrama](#bkmk_edit)  
  
 [Buscar tablas en un diagrama](#bkmk_findtables)  
  
 [Organizar los objetos de un diagrama](#bkmk_arrangeobjects)  
  
 [Conservar la organización de objetos](#bkmk_preserve)  
  
##  <a name="add-a-diagram"></a><a name="bkmk_add"></a>Agregar un diagrama  
 Los diagramas DSV se crean automáticamente al crear la DSV. Una vez creada la DSV, puede crear diagramas adicionales, quitarlos u ocultar objetos específicos para crear una representación de la DSV más fácil de administrar.  
  
 Para crear un diagrama, haga clic con el botón derecho en cualquier lugar del panel **Organizador de diagramas** y haga clic en **Nuevo diagrama**.  
  
 Al definir inicialmente una vista del origen de datos (DSV) en un proyecto de Analysis Services, todas las tablas y vistas agregadas a la vista del origen de datos se agregan al \<All Tables> diagrama. Este diagrama se muestra en el panel Organizador de diagramas del Diseñador de vistas del origen de datos. Las tablas de este diagrama (así como sus columnas y relaciones) se enumeran en el panel Tablas. Las tablas de este diagrama (así como sus columnas y relaciones) se muestran gráficamente en el panel Esquema. Sin embargo, a medida que se agregan tablas, vistas y consultas con nombre al \<All Tables> diagrama, el gran número de objetos de este diagrama dificulta la visualización de las relaciones, especialmente cuando se agregan varias tablas de hechos al diagrama y las tablas de dimensiones se relacionan con varias tablas de hechos.  
  
 Para que la visualización resulte más fácil si solo desea ver un subconjunto de las tablas de la vista del origen de datos, puede definir subdiagramas (que se denominan simplemente diagramas), formados por subconjuntos seleccionados de tablas, vistas y consultas con nombre de la vista del origen de datos. Puede utilizar los diagramas para agrupar elementos en la vista del origen de datos en función de sus necesidades empresariales o de soluciones.  
  
 Puede agrupar las tablas y consultas con nombre relacionadas en diagramas separados para fines empresariales y para facilitar la comprensión de una vista del origen de datos que contenga muchas tablas, vistas y consultas con nombre. Se puede incluir la misma tabla o consulta con nombre en varios diagramas, excepto en el \<All Tables> diagrama. En el \<All Tables> diagrama, todos los objetos contenidos en la vista del origen de datos se muestran exactamente una vez.  
  
##  <a name="edit-or-delete-a-diagram"></a><a name="bkmk_edit"></a>Editar o eliminar un diagrama  
 Cuando trabaje con un diagrama, preste especial atención a los comandos usados para agregar y quitar objetos. Por ejemplo, si elimina un objeto de un diagrama, dicho objeto también se eliminará de la DSV. Si solo desea eliminarlo del diagrama, use **Ocultar tabla** en su lugar.  
  
 ![Captura de pantalla del espacio de trabajo de diagrama, menú contextual](../media/ssas-olapdsv-diagram.gif "Captura de pantalla del espacio de trabajo de diagrama, menú contextual")  
  
 Aunque es posible ocultar objetos individualmente, al mostrarlos de nuevo mediante el comando Mostrar tablas relacionadas volverán a aparecer en el diagrama todos los objetos relacionados. Para controlar qué objetos se devuelven al área de trabajo, arrástrelos desde el panel Tablas.  
  
##  <a name="find-tables-in-a-diagram"></a><a name="bkmk_findtables"></a>Buscar tablas en un diagrama  
 Si el esquema tiene un gran tamaño, desplazarse hasta una tabla determinada del panel **Diagrama** puede resultar difícil. No obstante, las siguientes herramientas pueden facilitar la búsqueda de una tabla en un diagrama.  
  
-   Desplazarse por la lista de tablas en el panel **Tablas** .  
  
     Para incluir una tabla en el diagrama mostrado actualmente, arrastre la tabla desde el panel **Tablas** hasta el panel del diagrama.  
  
     Para centrar la presentación de una tabla que ya está incluida en el diagrama, seleccione la tabla en el panel **Tablas** .  
  
-   Localizador de tablas en el panel **Diagrama** : el localizador de tablas es un icono de flecha de 4 direcciones que se encuentra en la intersección de las barras de desplazamiento vertical y horizontal en la esquina inferior derecha del panel **Diagrama** . Abre una representación en miniatura del diagrama actual en el panel Diagrama. Puede usar esta miniatura para cambiar la vista del panel Diagrama a cualquier ubicación del diagrama.  
  
-   Use el cuadro de diálogo **Buscar tabla** : haga clic con el botón derecho en el área abierta del panel Diagrama y haga clic en **Buscar tabla**. O bien, haga clic en el comando **Buscar tabla** de la barra de herramientas o del menú **Vista del origen de datos** .  
  
     Puede escribir cadenas y caracteres comodín en el cuadro Filtro para ver subconjuntos de las tablas del diagrama.  
  
##  <a name="arrange-objects-in-a-diagram"></a><a name="bkmk_arrangeobjects"></a>Organizar los objetos de un diagrama  
 Aunque el Diseñador de vistas del origen de datos puede definir varios diagramas para que una DSV sea más comprensible, los diagramas que contienen docenas de tablas pueden resultar difíciles de leer y la reorganización manual del diseño de la tabla suele ser una tarea tediosa. El Diseñador de vistas del origen de datos puede reorganizar las tablas de forma automática en el diagrama actual usando un diseño rectangular o diagonal que se basa en las relaciones entre las tablas del diagrama.  
  
-   En un diseño rectangular, las líneas de relación se dibujan entre las tablas en lugar de hacerlo entre las columnas. Las líneas de relación se dibujan horizontal y verticalmente entre las tablas.  
  
-   En un diseño diagonal, las líneas de relación se dibujan tan directamente como sea posible entre las columnas relacionadas de las tablas. Una relación con varias columnas se adjunta a la primera columna relacionada de la tabla. Si las columnas de una tabla no son visibles, las líneas se dibujan en la parte superior de la tabla.  
  
##  <a name="preserve-object-arrangement"></a><a name="bkmk_preserve"></a>Conservar la organización de objetos  
 Una vez organizadas manualmente las tablas de la manera deseada, al agregar más tablas al diagrama se puede producir una actualización del mismo que quite las modificaciones realizadas recientemente a la disposición de los objetos.  
  
 Es más probable que este comportamiento se produzca al agregar una tabla, haciendo que el Organizador de diagramas mueva otras tablas para dar cabida a la nueva. Después vuelve a dibujar el diagrama para asegurarse de que todas las tablas y las líneas de conexión se representan correctamente. En este momento, se puede perder cualquier ajuste manual realizado en la posición de determinados objetos.  
  
 Para evitar este problema, agregue todas las tablas primero, antes de realizar los ajustes finales. Los objetos deben conservar ahora su posición en el diagrama cuando lo abra más adelante.  
  
## <a name="see-also"></a>Consulte también  
 [Vistas del origen de datos en modelos multidimensionales](data-source-views-in-multidimensional-models.md)   
 [Diseñador de vistas del origen de datos &#40;Analysis Services - Datos multidimensionales&#41;](../data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
