---
title: Requisitos previos del Asesor de actualizaciones | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672408"
---
# <a name="upgrade-advisor-prerequisites"></a>Requisitos previos del Asesor de actualizaciones
  En este tema se describen los requisitos de software para el Asesor de actualizaciones.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Los requisitos previos para instalar y ejecutar el Asesor de actualizaciones son los siguientes:  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] a partir de SP2, Windows 7 o [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.  
  
-   Windows Installer 4.5. Puede instalar Windows Installer desde el [sitio web de Windows Installer](https://www.microsoft.com/download/details.aspx?id=8483).  
  
-   [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], a partir de .NET Framework 4. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]Está disponible en los [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] medios del producto y en el [SDK, el redistribuible y Service Pack sitio web de descarga](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
    -   Para instalar .NET Framework 4 desde el disco de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], busque la raíz de la unidad de disco. A continuación, haga doble clic en la carpeta \redist, haga doble clic en la carpeta DotNetFrameworks y ejecute dotNetFx40_Full_x86_x64.exe (para sistemas operativos de 32 bits y 64 bits).  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom es un requisito previo para instalar el [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Asesor de actualizaciones y el programa de instalación del Asesor de actualizaciones no lo instala. El programa de instalación requiere que descargue e instale [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom desde el [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.  
  
## <a name="see-also"></a>Consulte también  
 [Procedimientos: Instalar el Asesor de actualizaciones](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
