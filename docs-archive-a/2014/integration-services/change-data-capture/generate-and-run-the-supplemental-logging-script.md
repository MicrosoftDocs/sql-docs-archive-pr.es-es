---
title: Generar y ejecutar el script de registro complementario | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1437a4b0f790376268095d8e52afa981af865b44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744272"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Generar y ejecutar el script de registro complementario
  Use la página Configurar tablas para capturar cambios con el fin de ejecutar un script en la base de datos de origen de Oracle que configurará el registro complementario.  
  
 **Para ejecutar los scripts de registro complementario**  
  
 Haga clic en **Ejecutar script** para ejecutar el script de registro complementario en las tablas definidas para la instancia CDC. Este script indica a la base de datos de Oracle que escriba todas las columnas de interés en sus registros de transacciones al registrar operaciones UPDATE en tablas capturadas. Normalmente es un administrador del sistema de Oracle quien examina y ejecuta este script.  
  
 También puede ejecutar los scripts manualmente mediante SQL * Plus.  
  
 **Para ejecutar los scripts manualmente**  
  
 Haga clic en **Copiar** para pegar el script en el Portapapeles. Abra SQL* Plus y vaya al directorio donde se encuentra la base de datos de origen de Oracle. Pegue el script en SQL\*Plus para ejecutarlo.  
  
 Para guardar el script de registro complementario en un archivo de texto, haga clic en **Guardar como** y vaya hasta la ubicación donde desee guardar el archivo. Asigne un nombre al archivo y haga clic en **Guardar** para guardar el archivo.  
  
 Haga clic en **Siguiente** para [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md).  
  
## <a name="see-also"></a>Consulte también  
 [Cómo crear la instancia de base de datos de cambios de SQL Server](how-to-create-the-sql-server-change-database-instance.md)   
 [Revisar y generar Scripts de registro complementario](review-and-generate-supplemental-logging-scripts.md)  
  
  
