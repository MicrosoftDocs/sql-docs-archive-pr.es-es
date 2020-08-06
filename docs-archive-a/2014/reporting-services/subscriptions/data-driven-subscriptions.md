---
title: Suscripciones controladas por datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: ba009f62-0d4f-45e7-a27c-36fd5f0cd3a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b59d5cc447191bef526d4cf4399a841d68932886
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671363"
---
# <a name="data-driven-subscriptions"></a>suscripciones controladas por datos
  Una suscripción controlada por datos proporciona una manera de utilizar datos de suscripción dinámica recuperados desde un origen de datos externo en tiempo de ejecución. Una suscripción controlada por datos también puede utilizar texto estático y valores predeterminados, que se especifican al definir la suscripción. Las suscripciones controladas por datos se pueden utilizar para:  
  
-   Distribuir un informe a una lista de suscriptores cambiante. Por ejemplo, puede utilizar las suscripciones controladas por datos para distribuir un informe en una organización de gran tamaño donde los suscriptores varíen de un mes a otro, o bien, puede utilizar otros criterios que determinen la pertenencia al grupo de un conjunto de usuarios existente.  
  
-   Filtrar la salida del informe utilizando valores de parámetro de informe recuperados en tiempo de ejecución.  
  
-   Modificar los formatos de salida y las opciones de entrega del informe para cada entrega de informe.  
  
 Una suscripción controlada por datos se compone de varias partes. Los aspectos fijos de una suscripción controlada por datos se definen al crear la suscripción; entre otros, se pueden citar los siguientes:  
  
-   El informe para el que se define la suscripción (una suscripción siempre se asocia a un solo informe).  
  
-   La extensión de entrega utilizada para distribuir el informe. Se puede especificar la entrega por correo electrónico del servidor de informes, la entrega a recursos compartidos de archivos, el proveedor de entrega NULL que se utiliza para la carga previa de la caché o una extensión de entrega personalizada. No se pueden especificar varias extensiones de entrega en una sola suscripción.  
  
-   El origen de datos de suscriptor. Al definir la suscripción, debe especificarse una cadena de conexión al origen de datos que contiene los datos de suscriptor. El origen de datos de suscriptor no se puede especificar dinámicamente en tiempo de ejecución.  
  
-   La consulta que se utiliza para seleccionar los datos de suscriptor debe especificarse al definir la suscripción. La consulta no se puede cambiar en tiempo de ejecución.  
  
 Los valores dinámicos que se utilizan en una suscripción controlada por datos se obtienen al procesar la suscripción. Algunos ejemplos de datos variables que se pueden utilizar en una suscripción son el nombre del suscriptor, la dirección de correo electrónico, el formato de salida preferido para el informe o cualquier valor que sea válido para un parámetro de informe. Para utilizar valores dinámicos en una suscripción controlada por datos se define una asignación entre los campos que se devuelven en la consulta y opciones de entrega específicas y parámetros de informe. Los datos variables se recuperan desde un origen de datos de suscriptor cada vez que se procesa la suscripción.  
  
## <a name="requirements-for-using-data-driven-subscriptions"></a>Requisitos para usar suscripciones controladas por datos  
 La funcionalidad de las suscripciones controladas por datos no está disponible en todas las ediciones. También existen limitaciones en cuanto a las clases de orígenes de datos que se pueden emplear para recuperar datos de suscripción en tiempo de ejecución. En la lista siguiente se ofrece más información acerca de los requisitos:  
  
-   Para obtener más información sobre las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que admiten la funcionalidad de suscripción controlada por datos, vea [características compatibles con las ediciones de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) ( https://go.microsoft.com/fwlink/?linkid=232473) .  
  
-   Para los datos de suscripciones, elija un origen de datos que pueda proporcionar información de esquema al servidor de informes. Los ejemplos de tipos de origen de datos compatibles incluyen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] los datos relacionales, Oracle, bases de datos [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] empaquetan datos, orígenes de datos ODBC y orígenes de datos OLE DB. Para más información sobre los requisitos del origen de datos de suscriptores, vea [Usar un origen de datos externo para obtener información de los suscriptores &#40;suscripción controlada por datos&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
## <a name="working-with-data-driven-subscriptions"></a>Trabajar con suscripciones controladas por datos  
 Los siguientes temas proporcionan más información sobre las suscripciones controladas por datos.  
  
|Temas|Descripción|  
|------------|-----------------|  
|[Crear, modificar y eliminar una suscripción controlada por datos](data-driven-subscriptions.md)|Explica cómo crear, modificar o eliminar una suscripción controlada por datos.|  
|[Usar un origen de datos externo para obtener información de los suscriptores &#40;suscripción controlada por datos&#41;](use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)|Proporciona información sobre los orígenes de datos que puede utilizar para una suscripción controlada por datos.|  
|[Crear una suscripción controlada por datos &#40;Tutorial de SSRS&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)|Proporciona instrucciones paso a paso para aprender a crear una suscripción controlada por datos.|  
|[Informes almacenados en caché &#40;SSRS&#41;](../report-server/caching-reports-ssrs.md)|Describe cómo utilizar el Proveedor de entrega NULL con una suscripción controlada por datos para cargar previamente la memoria caché.|  
  
## <a name="see-also"></a>Consulte también  
 [Suscripciones y entrega &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md)   
 [Página crear suscripción controlada por datos &#40;Administrador de informes&#41;](../create-data-driven-subscription-page-report-manager.md)   
 [Cargar previamente la memoria caché &#40;Administrador de informes&#41;](../report-server/preload-the-cache-report-manager.md)  
  
  
