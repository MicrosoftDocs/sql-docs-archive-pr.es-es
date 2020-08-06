---
title: Actualizar ensamblados de SQLCLR después de actualizar .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45d60db413e11828f26bd03e1c8f350645838d12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673911"
---
# <a name="upgrade-sqlclr-assemblies-after-net-framework-update"></a>Actualizar ensamblados de SQLCLR después de actualizar .NET Framework
  [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) es una colección de rutinas de Common Language Runtime de SQL (SQLCR) que hacen referencia a los ensamblados de Microsoft .NET Framework 4. Al instalar actualizaciones de .NET Framework en el equipo que afecten al ensamblado de .NET Framework al que hacen referencia, se producirá un cambio en el identificador de versión de módulos (MVID) del ensamblado en la memoria caché de ensamblados global (GAC). Esto produce una incoherencia entre los MVID del ensamblado al que se hace referencia en la GAC y el ensamblado de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si la actualización de .NET Framework requiere reiniciar el equipo [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , los ensamblados SQLCLR afectados se actualizan automáticamente para corregir el problema de discrepancia de MVID en el reinicio del equipo [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] . Sin embargo, para las actualizaciones de .NET Framework que no necesitan reiniciar el equipo con [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] , se produce un error debido a una discrepancia en los MVID de los ensamblados al intentar conectarse a un [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] mediante un [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]:  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe -upgradedlls.  
```  
  
 Para corregir este problema, deben actualizarse los ensamblados SQLCLR afectados en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Puede hacerlo ejecutando el archivo DQSInstaller.exe con el parámetro de línea de comandos **upgradedlls** para omitir la reconstrucción de las bases de datos de DQS y actualizar solo los ensamblados afectados. Esto garantiza que se conserven las bases de conocimiento, los proyectos de calidad de datos y otros datos de DQS.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Debe haber iniciado sesión como miembro del grupo Administradores en el equipo con [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
-   La cuenta de usuario de Windows debe ser miembro del rol fijo de servidor sysadmin en la instancia de SQL Server donde está instalado [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] .  
  
### <a name="to-upgrade-sqlclr-assemblies"></a>Para actualizar ensamblados de SQLCLR  
  
1.  Inicie el símbolo del sistema.  
  
2.  En el símbolo del sistema, cambie el directorio a la ubicación donde DQSInstaller.exe esté disponible. Si instaló la instancia predeterminada de SQL Server, el archivo DQSInstaller.exe estará disponible en C:\Archivos de programa\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  En el símbolo del sistema, escriba el siguiente comando y presione ENTRAR:  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  Todos los demás pasos son los mismos que los pasos 2 a 6 de la sección [Ejecutar DQSInstaller.exe desde la pantalla Inicio, el menú Inicio o el Explorador de Windows](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) de [Ejecutar DQSInstaller.exe para completar la instalación del servidor de calidad de datos](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
## <a name="see-also"></a>Consulte también  
 [Instalar Data Quality Services](install-data-quality-services.md)   
 [Actualizar el esquema de las bases de datos DQS tras instalar la actualización de SQL Server](upgrade-dqs-databases-schema-after-installing-sql-server-update.md)  
  
  
