---
title: PH timeout (opción de configuración del servidor) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 515ed74a4b92259d53770bf6d970626eba686453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744857"
---
# <a name="ph-timeout-server-configuration-option"></a>PH timeout (opción de configuración del servidor)
  Use la opción ph timeout para especificar el tiempo, en segundos, que el controlador de protocolo de texto completo debe esperar para conectarse a una base de datos antes de que se agote el tiempo de espera. El valor predeterminado es 60 segundos. Aumente el valor de ph timeout cuando se esté agotando el tiempo de espera de los intentos de conexión debido a problemas de red temporales.  
  
 El controlador de protocolo de texto completo se aloja en el host de demonio de filtro y se utiliza para capturar de SQL Server los datos cuyo índice de texto completo se va a crear. Para obtener más información sobre los componentes de búsqueda de texto completo, vea [Búsqueda de texto completo](../../relational-databases/search/full-text-search.md).  
  
 Al intentar capturar una fila de datos, si el controlador de protocolo no puede conectar con SQL Server dentro del tiempo especificado, notifica un error de tiempo de espera para esa fila. El recopilador de texto completo lo volverá a intentar más tarde. Para obtener más información sobre el recopilador de texto completo, vea [Rellenar índices de texto completo](../../relational-databases/indexes/indexes.md).  
  
## <a name="see-also"></a>Consulte también  
 [Búsqueda de texto completo](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
