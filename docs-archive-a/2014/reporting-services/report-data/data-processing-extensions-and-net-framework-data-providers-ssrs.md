---
title: Extensiones de procesamiento de datos y proveedores de datos de .NET Framework (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
- report data [Report Builder], accessing
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fd84af68af54b165c75317280bc19bb23da53366
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744516"
---
# <a name="data-processing-extensions-and-net-framework-data-providers-ssrs"></a>Extensiones de procesamiento de datos y proveedores de datos de .NET Framework (SSRS)
  Una extensión de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] es un componente instalado con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], diseñado para recuperar datos de un tipo de origen de datos específico y proporcionar una funcionalidad adicional para admitir el diseño y el procesamiento de informes. Una extensión de procesamiento de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] es un componente disponible de [!INCLUDE[msCoName](../../includes/msconame-md.md)] o de terceros que admite interfaces <xref:System.Data> que permiten recuperar y modificar datos de un tipo de origen de datos específico.  
  
## <a name="understanding-a-data-processing-extension"></a>Descripción de las extensiones de procesamiento de datos  
 Una extensión de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] admite un subconjunto de las interfaces de <xref:System.Data> . Las extensiones de procesamiento de datos solo requieren acceso de lectura a un origen de datos, de modo que no se implementen las interfaces para escritura y actualización. Cada extensión de procesamiento de datos puede incluir características personalizadas para admitir el procesamiento de informes. Por ejemplo, una extensión de procesamiento de datos podría admitir los tipos siguientes de características:  
  
-   Administración de credenciales independientemente de la cadena de conexión  
  
-   Admisión de parámetros de varios valores  
  
-   Recuperación de agregados de servidor, que se calculan en el origen de datos  
  
-   Recuperación de propiedades y valores de datos del origen de datos  
  
## <a name="understanding-a-data-provider"></a>Descripción de un proveedor de datos  
 Una extensión de procesamiento de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (a veces conocido como controlador) admite un conjunto estándar de las interfaces <xref:System.Data> para leer, escribir y actualizar datos en un origen de datos. Se puede usar un proveedor de datos cuando no hay ninguna extensión de procesamiento de datos disponible para un tipo específico de origen de datos. Hay disponibles diversos proveedores de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] de terceros.  
  
 Debido a que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] tiene una arquitectura de proveedor de datos extensible, puede generar una extensión de procesamiento de datos personalizada para incluir la funcionalidad adicional proporcionada por las extensiones de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Para obtener más información, vea [Implementing a Data Processing Extension](../extensions/data-processing/implementing-a-data-processing-extension.md). Para las extensiones de procesamiento de datos de terceros, vea la documentación incluida con ellas.  
  
> [!NOTE]  
>  Se debe instalar y registrar un proveedor de datos de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] o una extensión de procesamiento de datos personalizada para poder tener acceso a los datos de un origen de datos. La extensión de procesamiento de datos se debe instalar y registrar tanto en el cliente de informes para crear el informe como en el servidor de informes para ver el informe publicado. No todos los proveedores de datos están diseñados para funcionar en un entorno de servidor. Para más información, vea [Registrar un proveedor de datos estándar de .NET Framework &#40;SSRS&#41;](register-a-standard-net-framework-data-provider-ssrs.md) e [Implementar una extensión de procesamiento de datos](../extensions/data-processing/deploying-a-data-processing-extension.md).  
  
## <a name="see-also"></a>Consulte también  
 [Introducción a las extensiones de procesamiento de datos](../extensions/data-processing/data-processing-extensions-overview.md)   
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
