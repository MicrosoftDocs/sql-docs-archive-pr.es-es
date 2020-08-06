---
title: Comprobar archivos en uso | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccd65867-d4c0-43b2-8361-7fd41c6f79ac
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 51505b0dece146b7f6fcdf982e6f88a5715357e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672507"
---
# <a name="check-files-in-use"></a>Comprobar archivos en uso
  Para no tener que reiniciar Windows después de instalar las actualizaciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , use la página Comprobar archivos en uso con el fin de identificar los procesos que están bloqueando los archivos requeridos por el programa de instalación de la actualización de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Detenga todas las aplicaciones y servicios que establecen conexiones con las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se están actualizando. Se incluye la detención de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Si el programa de instalación determina que hay archivos bloqueados durante el proceso de instalación, puede que sea necesario reiniciar el equipo una vez completada la instalación. Si es necesario, el programa de instalación le indica que reinicie el equipo. Si el programa de instalación debe detener un servicio durante el proceso de instalación, lo reiniciará una vez completada la instalación.  
  
 Para eliminar el requisito de reinicio del equipo tras la instalación, el programa de instalación muestra una lista de los procesos que están bloqueando los archivos. Detenga o finalice los procesos y las aplicaciones de la lista. A continuación, haga clic en **Actualizar comprobación** para volver a ejecutar la comprobación. Haga clic en **Detener comprobación** para finalizar una comprobación que se esté ejecutando. Si no se encuentra ningún archivo bloqueado, la tabla está vacía. Cuando todos los procesos bloqueados se hayan cerrado o detenido, haga clic en **Siguiente** para continuar.  
  
 El programa de instalación registra la información en los archivos de registro. Para obtener más información sobre cómo ver los archivos de registro, vea [Ver y leer los archivos de registro de instalación de SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md) y [Cómo leer un archivo de registro de instalación de SQL Server](https://go.microsoft.com/fwlink/?LinkID=134490).  
  
 En el archivo de registro se incluye la información siguiente:  
  
-   Nombre del proceso  
  
-   Nombre de la característica de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Tipo de proceso  
  
-   Cuenta en la que se está ejecutando el proceso  
  
-   Identificador del proceso  
  
-   Nombre del archivo que está bloqueado  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
  
|Nombre|Descripción|  
|----------|-----------------|  
|Proceso|Muestra el nombre completo del proceso que está utilizando los archivos que se van a actualizar.|  
|Tipo|Muestra el tipo de proceso.|  
|Cuenta|Muestra la cuenta en la que se está ejecutando el proceso.|  
|Identificador del proceso|Muestra el identificador del proceso.|  
  
  
