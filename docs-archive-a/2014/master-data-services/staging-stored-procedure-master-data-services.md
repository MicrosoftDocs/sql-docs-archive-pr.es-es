---
title: Procedimiento almacenado de almacenamiento provisional (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9259352350a099db5d9b18411ad4da06dfb19819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677740"
---
# <a name="staging-stored-procedure-master-data-services"></a>Procedimiento almacenado de almacenamiento provisional (Master Data Services)
  Al iniciar el proceso de almacenamiento provisional desde [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], use uno de tres procedimientos almacenados.  
  
-   stg.udp_name_Leaf  
  
-   stg.udp_name_Consolidated  
  
-   stg.udp_name_Relationship  
  
 Donde name es el nombre de la tabla de ensayo que se especificó cuando se creó la entidad.  
  
## <a name="staging-process-stored-procedure-parameters"></a>Parámetros de los procedimientos almacenados del proceso de almacenamiento provisional  
 En la tabla siguiente se enumeran los parámetros de estos procedimientos almacenados.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**VersionName**<br /><br /> Obligatorio|El nombre de la versión. Puede distinguir mayúsculas de minúsculas o no, según la configuración de intercalación de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|**LogFlag**<br /><br /> Obligatorio|Determina si se registran o no las transacciones durante el proceso de almacenamiento provisional. Los valores posibles son:<br /><br /> **0**: no registrar transacciones.<br />**1**: registrar transacciones.<br /><br /> <br /><br /> Para obtener más información sobre las transacciones, consulte [Transacciones &#40;Master Data Services&#41;](transactions-master-data-services.md).|  
|**BatchTag**<br /><br /> Obligatorio, excepto para el servicio web|El valor de **BatchTag** como se especifica en la tabla de ensayo.|  
|**Batch_ID**<br /><br /> Solo lo necesita el servicio web|El valor de **Batch_ID** como se especifica en la tabla de almacenamiento provisional.|  
  
### <a name="staging-process-stored-procedure-example"></a>Ejemplo de procedimiento almacenado del proceso de almacenamiento provisional  
 En el ejemplo siguiente se muestra cómo iniciar el proceso de almacenamiento provisional mediante el procedimiento almacenado de almacenamiento provisional.  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a>Consulte también  
 [Master Data Services de &#40;de procedimiento almacenado de validación&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)   
 [Cargar o actualizar miembros en Master Data Services mediante el proceso de almacenamiento provisional](add-update-and-delete-data-master-data-services.md)   
 [Ver los errores que se producen durante el proceso de almacenamiento provisional &#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)  
  
  
