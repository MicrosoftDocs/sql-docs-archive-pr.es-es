---
title: Origen OData| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98b14ef034597f6098f70386ca41c1b90be86500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750037"
---
# <a name="odata-source"></a>Origen OData
  Use el componente de origen OData en un paquete SSIS para consumir datos de servicios de Open Data Protocol (OData). El componente admite los protocolos OData v2 y v3, así como los formatos de datos ATOM y JSON.  
  
> [!NOTE]  
>  El origen OData se puede usar para leer listas de SharePoint. Para ver todas las listas del servidor de SharePoint, use la siguiente dirección URL: http:// \<server> /_vti_bin/listdata.SVC. Para obtener más información sobre las convenciones de direcciones URL de SharePoint, vea [Interfaz de REST de SharePoint Foundation](https://msdn.microsoft.com/library/ff521587.aspx).  
  
## <a name="odata-format"></a>Formato OData  
 La mayoría de los servicios OData devuelven resultados en varios formatos. Puede especificar el formato del conjunto de resultados mediante la opción de consulta $format. Los formatos como JSON y JSON Light son más eficaces que ATOM/XML, y pueden conseguir mejor rendimiento cuando se transfieren grandes cantidades de datos. En la tabla siguiente se muestran resultados de pruebas de ejemplo. Como puede ver, hubo una mejora del rendimiento del 30-53 % al cambiar de ATOM a JSON y del 67 % cuando se cambió de ATOM al nuevo formato JSON Light (disponible en WCF Data Services 5.1).  
  
|||||  
|-|-|-|-|  
|Filas|ATOM|JSON|JSON (Light)|  
|10000|113 segundos|74 segundos|68 segundos|  
|1000000|1110 segundos|853 segundos|665 segundos|  
  
> [!NOTE]  
>  El origen OData de SSIS usa ODataLib 5.5.0 para analizar las fuentes OData y puede leer todos los formatos admitidos por esta biblioteca.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Instalar y desinstalar el Componente de origen OData](../install-and-uninstall-odata-source-component.md)  
  
-   [Tutorial: usar el origen OData &#91;SSIS&#93;](tutorial-using-the-odata-source.md)  
  
-   [Modificar una consulta de origen OData en tiempo de ejecución](modify-odata-source-query-at-runtime.md)  
  
-   [Editor de origen OData &#40;página Conexión&#41;](../odata-source-editor-connection-page.md)  
  
-   [Editor de origen OData &#40;página Columnas&#41;](../odata-source-editor-columns-page.md)  
  
-   [Editor de origen OData &#40;página Salida de error&#41;](../odata-source-editor-error-output-page.md)  
  
-   [Propiedades de orígenes OData](odata-source-properties.md)  
  
## <a name="see-also"></a>Consulte también  
 [Administrador de conexiones OData](../connection-manager/odata-connection-manager.md)  
  
  
