---
title: Conceptos de XMLA | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, concepts
ms.assetid: 816183a7-d2f7-4e14-8e5b-2a4c1798fbc1
author: minewiskan
ms.author: owend
ms.openlocfilehash: b2e18917b56d40f8b813ba10083cc1b408e51a98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675016"
---
# <a name="xmla-concepts"></a>Conceptos de XMLA
  El estándar abierto XML for Analysis admite el acceso a datos a orígenes de datos que residen en World Wide Web. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] implementa XMLA según la especificación XMLA 1,1.  
  
 XML for Analysis (XMLA) es un protocolo XML basado en SOAP (Protocolo simple de acceso a objetos), diseñado específicamente para el acceso universal a los datos de cualquier origen de datos multidimensionales estándar que resida en la Web. XMLA también elimina la necesidad de implementar un componente de cliente que exponga interfaces de modelo de objetos componentes (COM) o de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework. XMLA está optimizado para Internet, donde las idas y vueltas al servidor resultan costosas en términos de tiempo y recursos, y donde las conexiones con estado a un origen de datos pueden limitar las conexiones de usuario en el servidor.  
  
 XMLA es el protocolo nativo de, que se [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utiliza para toda interacción entre una aplicación cliente y una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] es plenamente compatible con XML for Analysis 1.1 y, además, proporciona extensiones para admitir la administración de metadatos y de sesiones e incluir capacidades de bloqueo. Tanto Objetos de administración de análisis (AMO) como ADOMD.NET utilizan el protocolo XMLA al comunicarse con una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="handling-xmla-communications"></a>Controlar las comunicaciones XMLA  
 El estándar abierto XMLA describe dos métodos accesibles a nivel general: `Discover` y `Execute`. Estos métodos utilizan la arquitectura de cliente y servidor de acoplamiento flexible admitida por XML para controlar la información de entrada y de salida en una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 El método `Discover` obtiene información y metadatos de un servicio web. Esta información puede incluir una lista de los orígenes de datos disponibles, así como información sobre cualquiera de los proveedores de orígenes de datos. Las propiedades definen y dan forma a los datos que se obtienen de un origen de datos. El método `Discover` es un método habitual para definir los numerosos tipos de información que una aplicación cliente puede requerir de los orígenes de datos en las instancias de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Las propiedades y la interfaz genérica proporcionan extensibilidad sin necesidad de volver a escribir las funciones existentes en una aplicación cliente.  
  
 El método `Execute` permite que las aplicaciones ejecuten comandos específicos del proveedor en orígenes de datos XMLA.  
  
 Aunque el protocolo XMLA está optimizado para las aplicaciones web, también se puede aprovechar para las aplicaciones orientadas a LAN. Pueden beneficiarse de esta API basada en XML las siguientes aplicaciones:  
  
-   Aplicaciones cliente/servidor que requieren una tecnología flexible entre los clientes y el servidor  
  
-   Aplicaciones cliente/servidor destinadas a diversos sistemas operativos  
  
-   Clientes que no requieren un estado relevante para aumentar la capacidad del servidor  
  
## <a name="xmla-and-the-unified-dimensional-model"></a>XMLA y el modelo UDM  
 XMLA es el protocolo que utilizan las aplicaciones de Business Intelligence que emplean la metodología del modelo UDM (Unified Dimensional Model).  
  
  
