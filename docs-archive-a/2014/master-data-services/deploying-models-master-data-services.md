---
title: Implementar modelos (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a9cc99112ec874e89ae07faa575235d9a041a972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87678226"
---
# <a name="deploying-models-master-data-services"></a>Implementar modelos (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], un paquete es un archivo XML que contiene una estructura del modelo implementable y, opcionalmente, los datos del modelo. Use los paquetes del modelo para mover las copias de modelos desde un entorno de MDS a otro, o para crear nuevos modelos en el entorno de MDS existente.  
  
> [!IMPORTANT]  
>  Los paquetes solamente se pueden implementar en la edición de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en la que se crearon. Esto significa que los paquetes que se hayan creado en [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] no se pueden implementar en [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] o posterior.  
  
## <a name="tools-for-deploying-models"></a>Herramientas para implementar modelos  
 Para trabajar con paquetes de modelos, puede usar una de tres herramientas, dependiendo de sus necesidades.  
  
-   **Herramienta MDSModelDeploy**: para crear e implementar objetos y datos del modelo, use la herramienta MDSModelDeploy.exe. Si seleccionó la ruta de acceso predeterminada al instalar MDS, esta herramienta se encuentra en *unidad*: \Archivos de Programa\microsoft SQL Server\120\Master Data Services\Configuration.  
  
-   **Asistente para implementación de modelos**: para crear e implementar paquetes de la estructura del modelo únicamente, use el asistente de la aplicación web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . No puede usar este asistente para la implementación de datos.  
  
-   **Modelo editor de paquetes**: para modificar un modelo de paquetes, use ModelPackageEditor.exe que inicia el asistente de modelo editor de paquetes. Utilice este asistente para modificar un paquete que haya creado la herramienta MDSModelDeploy o el asistente para implementación de modelos. Si seleccionó la ruta de acceso predeterminada al instalar MDS, esta herramienta se encuentra en *unidad*: \Archivos de Programa\microsoft SQL Server\120\Master Data Services\Configuration.  
  
> [!IMPORTANT]  
>  Puede usar MDSDeployModel para crear un nuevo modelo, crear un clon de un modelo o actualizar un modelo existente y sus datos. Si usa la herramienta MDSModelDeploy para actualizar un modelo existente y sus datos, y el paquete no contiene una entidad, un atributo o un miembro que exista en el modelo de destino, MDSModelDeploy no eliminará dicha entidad, atributo o miembro del modelo.  
  
## <a name="what-packages-contain"></a>Qué contienen los paquetes  
 Un paquete del modelo es un archivo XML que se guarda con la extensión .pkg. Al crear un paquete de implementación, puede decidir si va a incluir o no datos. Si decide incluir los datos, debe seleccionar una versión de los datos que se incluirán.  
  
 Todos los objetos del modelo se incluyen en un paquete. Estos objetos son:  
  
-   Entidades  
  
-   Atributos  
  
-   Grupos de atributos  
  
-   Jerarquías  
  
-   Colecciones  
  
-   Reglas de negocios  
  
-   Marcas de versión  
  
-   Vistas de suscripciones  
  
 Los metadatos definidos por el usuario, atributos de archivo y permisos de usuario y de grupo no se incluyen. Después de implementar un modelo, debe actualizarlos manualmente.  
  
## <a name="sample-packages"></a>Paquetes de ejemplos  
 Cuando se instala [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]se incluyen archivos de paquete de ejemplo. Estos archivos de paquete están en el directorio Master Data Services\Samples\Packages de la instalación de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Cuando se implementan estos paquetes de muestra con la herramienta MDSModelDeploy, se crean modelos de ejemplo y se rellenan con datos.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Crear un nuevo paquete de implementación de objetos o datos del modelo mediante la herramienta MDSModelDeploy.|[Crear un paquete de implementación de modelo mediante MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Crear un nuevo paquete de implementación de objetos del modelo solo con el asistente.|[Crear un paquete de implementación de modelo mediante el asistente](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|Implementar un paquete de objetos y datos del modelo mediante la herramienta MDSModelDeploy.|[Implementar un paquete de implementación de modelo mediante MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Implementar un paquete de objetos del modelo solo con el asistente.|[Implementar un paquete de implementación de modelo mediante el asistente](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|Modifique un paquete de implementación de modelos para implementar porciones seleccionadas de un modelo, en lugar del modelo en su totalidad.|[Editar un paquete de implementación de modelos](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
  
-   [Opciones de la implementación de modelos &#40;Master Data Services&#41;](model-deployment-options-master-data-services.md)  
  
  
