---
title: Elementos de informe personalizados | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86b819cb4d305e537a52a2e7f25cdfa3aefa5f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750533"
---
# <a name="custom-report-items"></a>Elementos de informe personalizados
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] proporciona un abundante conjunto de herramientas para crear y publicar informes de empresa, administrar la seguridad y las suscripciones, y extender la funcionalidad de informes a través de una completa API. Los informes se definen utilizando un lenguaje basado en XML denominado lenguaje RDL (Report Definition Language). RDL proporciona un conjunto de instrucciones que describen el diseño, la información de las consultas y los tipos de elementos de un informe. Se puede extender RDL escribiendo un elemento de informe personalizado. El elemento de informe personalizado consta de un componente de tiempo de ejecución, que se denomina procesador de informes en tiempo de ejecución, y un componente de tiempo de diseño, que permite al elemento de informe personalizado estar disponible en el Diseñador de informes.  
  
 Para obtener un ejemplo de un elemento de informe personalizado totalmente implementado, vea [Ejemplos del producto SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="custom-report-item-scenarios"></a>Escenarios de elementos de informe personalizado  
 Los desarrolladores de software que necesitan integrar [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en sus aplicaciones pueden requerir alguna funcionalidad que no se admita de forma nativa en RDL. Esto puede incluir elementos como controles de mapas, listas horizontales, listas de columnas y matrices dinámicas. Un componente de elemento de informe personalizado de tiempo de ejecución se puede desarrollar y distribuir con una aplicación para cubrir esta necesidad.  
  
 Además de proporcionar una funcionalidad que no se admita de forma nativa, algunos programadores pueden querer extender la funcionalidad existente con versiones alternativas de controles que ya están incluidos con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. En este escenario, un programador podría proporcionar tres componentes: un componente de tiempo de ejecución, un componente de tiempo de diseño y un componente de conversión de elementos de informe de tiempo de diseño que convierte un elemento de informe existente en un elemento de informe personalizado a petición.  
  
## <a name="in-this-section"></a>En esta sección  
 [Arquitectura de elementos de informe personalizados](custom-report-item-architecture.md)  
 Describe los componentes que constituyen un elemento de informe personalizado.  
  
 [Requisitos de implementación de elementos de informe personalizados](custom-report-item-implementation-requirements.md)  
 Describe los requisitos previos para crear un elemento de informe personalizado.  
  
 [Crear un componente de tiempo de ejecución de elemento de informe personalizado](creating-a-custom-report-item-run-time-component.md)  
 Describe cómo crear un componente de tiempo de ejecución de elementos de informe personalizado.  
  
 [Crear un componente de tiempo de diseño de elemento de informe personalizado](creating-a-custom-report-item-design-time-component.md)  
 Describe cómo crear un componente de tiempo de diseño de elementos de informe personalizado.  
  
 [Cómo: Implementar un elemento de informe personalizado](how-to-deploy-a-custom-report-item.md)  
 Describe cómo implementar un elemento de informe personalizado.  
  
 [Bibliotecas de clases de elemento de informe personalizado](custom-report-item-class-libraries.md)  
 Describe las clases de infraestructuras de los elementos de informe personalizados y las clases contenedoras administradas en el espacio de nombres `Microsoft.ReportDesigner`.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia técnica &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
