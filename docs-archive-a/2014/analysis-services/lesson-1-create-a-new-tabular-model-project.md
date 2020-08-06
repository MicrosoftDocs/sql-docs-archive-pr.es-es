---
title: 'Lección 1: crear un nuevo proyecto de modelo tabular | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8b18c18116d5a9dacdf49fe23f4f545bb3a0f987
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87749528"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>Lección 1: Crear un nuevo proyecto de modelo tabular
  En esta lección, creará un nuevo proyecto de modelo tabular en blanco en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Una vez creado el nuevo proyecto, puede comenzar a agregar datos usando el Asistente para la importación de tablas. Además de crear un nuevo proyecto, esta lección incluye también una breve introducción al entorno de creación de modelos tabulares en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
 Para obtener más información sobre los diferentes tipos de proyectos de modelos tabulares, vea [Proyectos de modelos tabulares &#40;SSAS tabular&#41;](tabular-models/tabular-model-projects-ssas-tabular.md). Para obtener más información sobre el entorno de creación de modelos tabulares, vea [Diseñador de modelos tabulares &#40;&#41;tabulares de SSAS ](tabular-model-designer-ssas-tabular.md).  
  
 Tiempo estimado para completar esta lección: **10 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
 Este tema es la primera lección de un tutorial de creación de modelos tabulares. Para completar esta lección, debe tener la base de datos AdventureWorksDW instalada en una instancia de SQL Server. Para obtener más información, vea [Creación de modelos tabulares &#40;tutorial de Adventure Works&#41;](tabular-modeling-adventure-works-tutorial.md).  
  
## <a name="create-a-new-tabular-model-project"></a>Crear un nuevo proyecto de modelo tabular  
  
#### <a name="to-create-a-new-tabular-model-project"></a>Para crear un proyecto de modelo tabular  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], en el menú **Archivo** , haga clic en **Nuevo**y, a continuación, en **Proyecto**.  
  
2.  En el cuadro de diálogo **nuevo proyecto** , en **plantillas instaladas**, haga clic en **Business Intelligence**, haga clic en **Analysis Services**y, a continuación, haga clic en **Analysis Services proyecto tabular**.  
  
3.  En **nombre**, escriba `AW Internet Sales Tabular Model` y, a continuación, especifique una ubicación para los archivos de proyecto.  
  
     De forma predeterminada, **Nombre de la solución** será el mismo que el nombre del proyecto, aunque puede escribir otro nombre para la solución.  
  
4.  Haga clic en **OK**.  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a>Descripción del entorno de creación de modelos tabulares con las herramientas de datos de SQL Server  
 Ahora que ha creado un nuevo proyecto de modelo tabular, dedique un momento a explorar el entorno de creación de modelos tabulares de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] (Visual Studio 2010 o posterior).  
  
 Después de crear el proyecto, este se abre en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Aparecerá un modelo vacío en el diseñador de modelos y el archivo **Model.bim** se seleccionará en la ventana **Explorador de soluciones** . Cuando agregue datos, aparecerán tablas y columnas en el diseñador. Si no ve el diseñador (la ventana vacía con la pestaña Model. BIM), en **Explorador de soluciones**, en `AW Internet Sales Tabular Model` , haga doble clic en el archivo **Model. BIM** .  
  
 Puede ver las propiedades básicas del proyecto en la ventana **Propiedades** . En **Explorador de soluciones**, haga clic en `AW Internet Sales Tabular Model` . Observe que en la ventana **Propiedades** , en **Archivo de proyecto**, aparece **Modelo tabular de ventas por Internet de AW.smproj**. Este es el nombre de archivo del proyecto. En **Carpeta del proyecto**, verá la ubicación del archivo del proyecto.  
  
 En **Explorador de soluciones**, haga clic con el botón secundario en el `AW Internet Sales Tabular Model` proyecto y, a continuación, haga clic en **propiedades**. Aparece el cuadro de diálogo **Páginas de propiedades del Modelo tabular de ventas por Internet de AW** . Estas son las propiedades avanzadas del proyecto. Establecerá alguna de estas propiedades más adelante cuando esté preparado para implementar el modelo.  
  
 Ahora, echemos un vistazo a las propiedades del modelo. En el **Explorador de soluciones**, haga clic en **Model.bim**. En la ventana **Propiedades** verá ahora las propiedades del modelo, de las cuales la más importante es **Modo DirectQuery** . Esta propiedad especifica si el modelo se implementa o no en modo en memoria (desactivado) o en modo DirectQuery (activado). En este tutorial, creará e implementará el modelo en modo de almacenamiento en memoria.  
  
 Cuando crea un modelo nuevo, algunas propiedades del modelo se establecen automáticamente según la configuración del modelo de datos, que puede especificarse en Herramientas\cuadro de diálogo Opciones. Las propiedades Copia de seguridad de datos, Retención de área de trabajo y Servidor del área de trabajo especifican cómo y dónde se realiza una copia de seguridad, se conserva en memoria y se crea la base de datos del área de trabajo (la base de datos de creación del modelo). Si es necesario, puede cambiar estas opciones más adelante, pero de momento dejaremos estas propiedades tal como están.  
  
 Cuando instaló [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], se agregaron varios elementos de menú nuevos al entorno de Visual Studio. Echemos un vistazo a los nuevos elementos de menú que son específicos de la creación de modelos tabulares. Haga clic en el menú **Modelo**. Desde aquí, puede iniciar el Asistente para la importación de tablas, ver y editar conexiones existentes, actualizar los datos del área de trabajo, examinar el modelo en [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel con la característica Analizar de Excel, crear perspectivas y roles, seleccionar la vista del modelo y definir opciones de cálculo.  
  
 Haga clic en el menú **Tabla** . Aquí puede crear y administrar las relaciones entre tablas, crear y administrar tablas, especificar la configuración de las tablas de datos, crear particiones y editar las propiedades de tabla.  
  
 Haga clic en el menú **Columna** . Aquí puede agregar y eliminar columnas de una tabla, inmovilizar columnas y especificar el criterio de ordenación. También puede utilizar la característica de autosuma para crear una medida de agregación estándar para una columna seleccionada. Otros botones de la barra de herramientas proporcionan acceso rápido a características y comandos usados con frecuencia.  
  
 Examine algunos de los cuadros de diálogo y ubicaciones de las distintas características específicas de la creación de modelos tabulares. Aunque algunos elementos aún no estén activos, puede hacerse una idea de cómo es el entorno de creación de modelos tabulares.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para continuar este tutorial, vaya a la lección siguiente: [Lección 2: Agregar datos](lesson-2-add-data.md).  
  
  
