---
title: Establecer o cambiar el método de conexión preferido para DirectQuery | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f10d5678-d678-4251-8cce-4e30cfe15751
author: minewiskan
ms.author: owend
ms.openlocfilehash: 239c80ace0daa3498c8dafd8fea358ce540931d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748298"
---
# <a name="set-or-change-the-preferred-connection-method-for-directquery"></a>Establecer o cambiar el método de conexión preferido para DirectQuery
  Al crear un modelo para utilizarlo en el modo DirectQuery, primero debe configurar el entorno de diseño para que admita el uso de DirectQuery. Para ello, vea [Habilitar el modo de diseño de DirectQuery &#40;&#41;tabular de SSAS ](tabular-models/enable-directquery-mode-in-ssdt.md).  
  
 Cuando esté en disposición de implementar el modelo, deberá establecer ciertas propiedades adicionales para permitir el acceso de los usuarios al modelo mediante uno de los modos DirectQuery:  
  
-   Debe indicar si las consultas realizadas en el modelo deben utilizar los datos en caché o el origen de datos relacional. Puede utilizar un modo híbrido o Solo DirectQuery.  
  
-   Si utiliza particiones, debe indicar qué partición desea usar como el origen de datos DirectQuery.  
  
-   Debe establecer las opciones de suplantación para los usuarios que van a tener acceso al origen de datos de SQL Server.  
  
 En este procedimiento se describe cómo establecer el método de conexión preferido para un modelo DirectQuery en el diseñador. También se describe cómo cambiar esta propiedad en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] una vez implementado el modelo.  
  
### <a name="to-set-the-preferred-connection-method-for-a-directquery-model"></a>Para establecer el método de conexión preferido para un modelo DirectQuery  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], abra el archivo de solución para el modelo DirectQuery.  
  
2.  En el menú **Proyecto** de Visual Studio, seleccione **Propiedades**.  
  
3.  En el panel **Propiedades** , cambie la propiedad **DirectQueryMode**a uno de los valores que admita el uso de DirectQuery:  
  
    -   **InMemory con DirectQuery**: si utiliza esta opción, el modelo se implementará, pero deberá procesar la memoria caché para poder ejecutar consultas en él.  
  
    -   **DirectQuery con InMemory**: si utiliza esta opción, la caché estará disponible para los clientes si ya se ha procesado. Si implementa el modelo con esta configuración y no procesa la caché, algunos clientes obtendrán un error al intentar conectarse con el modelo.  
  
    -   **Solo DirectQuery**: si utiliza esta opción, los metadatos se implementarán pero el modelo no contendrá ningún dato. Los clientes que intenten conectarse mediante el modo en memoria obtendrán un error que indicará que el modelo no existe o que no se ha procesado.  
  
4.  Si hay errores, abra la **Lista de errores** en Visual Studio y solucione los problemas que impiden que el modelo se implemente en el modo DirectQuery.  
  
### <a name="to-verify-or-change-the-preferred-connection-method-for-a-directquery-model"></a>Para comprobar o cambiar el método de conexión preferido para un modelo DirectQuery  
  
1.  En [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], conéctese con la instancia en la que implementó el modelo DirectQuery.  
  
2.  Haga clic con el botón secundario del mouse en la base de datos del modelo y seleccione **Propiedades**.  
  
3.  En el panel **Propiedades** , cambie la propiedad **DirectQueryMode**a uno de los valores siguientes:  
  
    -   **Solo DirectQuery**  
  
    -   **InMemory con DirectQuery**  
  
    -   **DirectQuery con inmemory**  
  
 Observe que estas propiedades son las mismas que las que estableció en el proyecto antes de la implementación en Visual Studio. Puede cambiar el método de conexión preferido para el modelo DirectQuery en cualquier momento, siempre que haya configurado el modelo para que admita el uso de DirectQuery.  
  
## <a name="see-also"></a>Consulte también  
 [Modo DirectQuery &#40;&#41;tabular de SSAS](tabular-models/directquery-mode-ssas-tabular.md)   
 [Habilitar el modo de diseño DirectQuery &#40;SSAS tabular&#41;](tabular-models/enable-directquery-mode-in-ssdt.md)  
  
  
