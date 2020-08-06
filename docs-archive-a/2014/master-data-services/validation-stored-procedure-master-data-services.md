---
title: Procedimiento almacenado de validación (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8fa6b01d950c87768d10b0252c1ccbab2b932fe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673060"
---
# <a name="validation-stored-procedure-master-data-services"></a>Procedimiento almacenado de validación (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], valide una versión para aplicar las reglas de negocios a todos los miembros de la versión del modelo.  
  
 En este tema se explica cómo usar el procedimiento almacenado **mdm.udpValidateModel** para validar datos. Si es administrador de la aplicación web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , puede realizar la validación en la interfaz de usuario en su lugar. Para obtener más información, consulte [Validar una versión con las reglas de negocios &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  Si invoca la validación antes de que se complete el proceso de almacenamiento provisional, no se validarán los miembros que no se hayan terminado de almacenar.  
  
## <a name="example"></a>Ejemplo  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>Parámetros  
 Los parámetros de este procedimiento son los siguientes:  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|UserID|Id. de usuario.|  
|Model_ID|Identificador del modelo.|  
|Version_ID|Identificador de versión.|  
  
## <a name="see-also"></a>Consulte también  
 [Master Data Services de &#40;de importación de datos&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Validar una versión con las reglas de negocios &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)  
  
  
