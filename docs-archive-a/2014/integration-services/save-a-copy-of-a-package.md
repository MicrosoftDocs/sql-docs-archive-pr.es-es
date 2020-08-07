---
title: Guardar una copia de un paquete | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 02ee2374fddb7dbb6b17adc2a4a10707179c882d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745374"
---
# <a name="save-a-copy-of-a-package"></a>Guardar una copia de un paquete
  Este procedimiento describe cómo guardar una copia de un paquete en el sistema de archivos, en el almacén de paquetes o en la base de datos **msdb** en [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Al especificar una ubicación para guardar la copia del paquete, puede actualizar también el nombre del paquete.  
  
 El almacén de paquetes puede incluir la base de datos **msdb** y las carpetas del sistema de archivos, solamente la base de datos **msdb**o solamente las carpetas del sistema de archivos. En **msdb**, los paquetes se guardan en la tabla **sysssispackages** . Esta tabla incluye una columna **folderid** que identifica la carpeta lógica a la que pertenece el paquete. Las carpetas lógicas proporcionan una forma útil de agrupar paquetes guardados en **msdb** del mismo modo que las carpetas del sistema de archivos proporcionan una forma de agrupar paquetes guardados en el sistema de archivos. Las filas en la tabla **sysssispackagefolders** en **msdb** definen las carpetas.  
  
 Si **msdb** no está definida como parte del almacén de paquetes, puede continuar asociando paquetes con carpetas lógicas existentes cuando seleccione SQL Server en la opción **Ruta de acceso del paquete** .  
  
> [!NOTE]  
>  El paquete se debe abrir en el Diseñador [!INCLUDE[ssIS](../includes/ssis-md.md)] para poder guardar una copia del paquete.  
  
### <a name="to-save-a-copy-of-a-package"></a>Para guardar una copia de un paquete  
  
1.  En el Explorador de soluciones, haga doble clic en el paquete cuya copia desea guardar.  
  
2.  En el menú **Archivo**, haga clic en **Guardar copia de \<package file> como**.  
  
3.  En el cuadro de diálogo **Guardar copia del paquete** , seleccione una ubicación de paquete en la lista **Ubicación del paquete** .  
  
4.  Si la ubicación es **SQL Server** o **Almacén de paquetes SSIS**, proporcione un nombre de servidor.  
  
5.  Si se guarda en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], especifique el tipo de autenticación y, si se usa la Autenticación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , proporcione un nombre de usuario y una contraseña.  
  
6.  Para especificar la ruta de acceso del paquete, escríbala o haga clic en el botón Examinar **(…)** para especificar la ubicación del paquete. El nombre predeterminado del paquete es Paquete. Opcionalmente, cambie el nombre del paquete a uno que satisfaga sus necesidades.  
  
     Si selecciona **SQL Server** como opción de **Ruta de acceso del paquete** , la ruta de acceso del paquete consta de carpetas lógicas de **msdb** y el nombre del paquete. Por ejemplo, si el paquete DownloadMonthlyData está asociado con la carpeta Finance dentro de la carpeta MSDB (nombre predeterminado de la carpeta lógica raíz de **msdb**), la ruta del paquete DownloadMonthlyData es MSDB/Finance/DownloadMonthlyData.  
  
     Si selecciona **Almacén de paquetes SSIS** como opción de **Ruta de acceso del paquete** , la ruta del paquete consta de la carpeta que administra el servicio Integration Services. Por ejemplo, si el paquete UpdateDeductions se encuentra en la carpeta HumanResources dentro de la carpeta del sistema de archivos que administra el servicio, la ruta del paquete es /File System/HumanResources/UpdateDeductions; de igual modo, si el paquete PostResumes está asociado con la carpeta HumanResources dentro de la carpeta MSDB, la ruta de acceso del paquete es MSDB/HumanResources/PostResumes.  
  
     Si selecciona **Sistema de archivos** como opción de **Ruta de acceso del paquete** , la ruta del paquete es la ubicación en el sistema de archivos y el nombre de archivo. Por ejemplo, si el nombre del paquete es UpdateDemographics, la ruta del paquete es C:\HumanResources\Quarterly\UpdateDemographics.dtsx.  
  
7.  Revise el nivel de protección del paquete.  
  
8.  También puede hacer clic en el botón Examinar **(…)** junto al cuadro **Nivel de protección** para cambiar el nivel de protección.  
  
    -   En el cuadro de diálogo **Nivel de protección de paquetes** , seleccione un nivel de protección diferente.  
  
    -   Haga clic en **OK**.  
  
9. Haga clic en **OK**.  
  
## <a name="see-also"></a>Consulte también  
 [Integration Services &#40;paquetes&#41; SSIS](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Configurar el servicio Integration Services &#40;servicio SSIS&#41;](service/integration-services-service-ssis-service.md)  
  
  
