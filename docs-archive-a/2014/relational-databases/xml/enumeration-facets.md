---
title: Facetas de enumeración | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e06598890d9b652879327e0351db5113cc17e6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662696"
---
# <a name="enumeration-facets"></a><span data-ttu-id="4e3ea-102">facetas de enumeración</span><span class="sxs-lookup"><span data-stu-id="4e3ea-102">Enumeration Facets</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4e3ea-103">rechaza los esquemas XML con tipos que tienen facetas de patrón o enumeraciones que infringen estas facetas.</span><span class="sxs-lookup"><span data-stu-id="4e3ea-103">rejects XML schemas with types that have pattern facets or enumerations that violate those facets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e3ea-104">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4e3ea-104">Example</span></span>  
 <span data-ttu-id="4e3ea-105">El esquema siguiente se verá rechazado porque su valor de enumeración incluye un valor con mayúsculas y minúsculas mezcladas.</span><span class="sxs-lookup"><span data-stu-id="4e3ea-105">The following schema would be rejected, because the featured enumeration value includes a mixed-case value.</span></span> <span data-ttu-id="4e3ea-106">También se rechazará porque infringe el valor de patrón que limita los valores únicamente a letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="4e3ea-106">It would also be rejected because this value violates the pattern value that limits values to only lowercase letters.</span></span>  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e3ea-107">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4e3ea-107">See Also</span></span>  
 [<span data-ttu-id="4e3ea-108">Requisitos y limitaciones de las colecciones de esquemas XML en el servidor</span><span class="sxs-lookup"><span data-stu-id="4e3ea-108">Requirements and Limitations for XML Schema Collections on the Server</span></span>](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  