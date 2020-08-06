---
title: Copia de bases de datos en otros servidores | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bcde6185f25129596b4be7a150d4ee230c54c1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745818"
---
# <a name="copy-databases-to-other-servers"></a>Copiar bases de datos en otros servidores
  En ocasiones resulta útil copiar una base de datos de un equipo a otro para realizar pruebas, comprobar la coherencia, desarrollar software, ejecutar informes, crear una base de datos de reflejo o, quizás, poner la base de datos a disposición de las actividades de oficinas remotas.  
  
 Hay varias maneras de copiar una base de datos:  
  
-   Usar el Asistente para copiar bases de datos  
  
     Puede usar el Asistente para copiar bases de datos con el fin de copiar o mover bases de datos entre los servidores o actualizar una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a una versión posterior. Para más información, consulte [Use the Copy Database Wizard](use-the-copy-database-wizard.md).  
  
-   Restaurar una copia de seguridad de una base de datos  
  
     Para copiar una base de datos completa, puede utilizar las instrucciones BACKUP y RESTORE de [!INCLUDE[tsql](../../includes/tsql-md.md)] . Normalmente, la restauración de una copia de seguridad completa de una base de datos se utiliza para copiar la base de datos de un equipo a otro por varios motivos. Para obtener más información sobre el uso de copias de seguridad y restauración para copiar una base de datos, vea [Copiar bases de datos con Copias de seguridad y restauración](copy-databases-with-backup-and-restore.md).  
  
    > [!NOTE]  
    >  Para configurar una base de datos reflejada para la creación de reflejo de la base de datos, debe restaurar la base de datos en el servidor reflejado mediante RESTORE DATABASE *<nombre_de_base_de_datos>* WITH NORECOVERY. Para obtener más información, vea [Preparar una base de datos reflejada para la creación de reflejo &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Utilizar el asistente Generar scripts para publicar bases de datos  
  
     Puede utilizar el asistente Generar scripts para transferir una base de datos de un equipo local a un proveedor de hospedaje web. Para obtener más información, vea [Asistente Generar y publicar scripts](../scripting/generate-and-publish-scripts-wizard.md).  
  
  
