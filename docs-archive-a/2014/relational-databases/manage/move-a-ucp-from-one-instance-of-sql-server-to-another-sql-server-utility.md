---
title: Movimiento de un UCP desde una instancia de SQL Server a otra (utilidad de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2cf17a79c9a1bb1bd7e86e1ecb36ef671414fb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672958"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a>Mover un UCP desde una instancia de SQL Server a otra (utilidad de SQL Server)
  En este tema se describe cómo mover un punto de control de la utilidad (UCP) de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a otra en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a>Mover un UCP desde una instancia de SQL Server a otra.  
  
1.  Cree un nuevo UCP en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , que será la nueva instancia del host del UCP. Para obtener más información, vea [Crear un punto de control de la Utilidad de SQL Server &#40;Utilidad de SQL Server&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md).  
  
2.  Si se ha establecido la configuración de la directiva no predeterminada para alguna de las instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en su utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tome nota de los umbrales de la directiva, de forma que pueda restablecerlos en el UCP nuevo. Las directivas predeterminadas se aplicarán cuando se agreguen las instancias al UCP nuevo. Si las directivas predeterminadas están en vigor, la vista de lista de la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mostrará **Global** en la columna **Tipo de directiva** .  
  
3.  Quite todas las instancias administradas del UCP anterior. Para obtener más información, vea [Quitar una instancia de SQL Server de la Utilidad de SQL Server](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
4.  Haga una copia de seguridad del almacén de administración de datos de la utilidad (UMDW) del UCP anterior. El nombre de archivo es Sysutility_mdw_\<GUID>_DATA y la ubicación predeterminada de la base de datos es \<System drive>:\Archivos de programa\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, donde \<System drive> es, por lo general, la unidad C:\. Para obtener más información, vea [Copiar bases de datos con Copias de seguridad y restauración](../databases/copy-databases-with-backup-and-restore.md).  
  
5.  Restaure la copia de seguridad del UMDW en el nuevo UCP. Para obtener más información, vea [Copiar bases de datos con Copias de seguridad y restauración](../databases/copy-databases-with-backup-and-restore.md).  
  
6.  Inscriba las instancias en el nuevo UCP para que las administre la utilidad de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para obtener más información, vea [Inscribir una instancia de SQL Server &#40;Utilidad de SQL Server&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md).  
  
7.  Implemente las definiciones de la directiva personalizada para las instancias administradas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], según sea necesario.  
  
8.  Espere aproximadamente 1 hora para que se completen las operaciones de recopilación e incorporación de datos.  
  
9. Para actualizar los datos, haga clic con el botón derecho en el nodo **Instancias administradas** en **Explorador de la utilidad**y, luego, seleccione **Actualizar**. Los datos de la vista de lista se muestran en el panel de contenido de **Explorador de la utilidad** . Para obtener más información, vea [Ver los resultados de la directiva de mantenimiento de recursos &#40;Utilidad de SQL Server&#41;](view-resource-health-policy-results-sql-server-utility.md).  
  
## <a name="see-also"></a>Consulte también  
 [Características y tareas de la utilidad de SQL Server](sql-server-utility-features-and-tasks.md)   
 [Inscribir una instancia de SQL Server &#40;Utilidad de SQL Server&#41;](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  
