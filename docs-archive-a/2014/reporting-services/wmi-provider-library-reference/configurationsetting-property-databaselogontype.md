---
title: Propiedad DatabaseLogonType (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3bb5a4149c29fb7532b7140a2616dd856e6db2b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748551"
---
# <a name="databaselogontype-property-wmi-msreportserver_configurationsetting"></a>Propiedad DatabaseLogonType (WMI MSReportServer_ConfigurationSetting)
  Especifica si el servidor de informes usa una cuenta de servicio de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, una cuenta de usuario de Windows o un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para tener acceso a la base de datos del servidor de informes. Solo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Valores de propiedad  
 Un objeto `integer` que representa el tipo de inicio de sesión.  
  
## <a name="example-code"></a>Código de ejemplo  
 [Clase MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Observaciones  
 Los valores son:  
  
-   0 para el inicio de sesión de Windows  
  
-   1 para el inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 para el inicio de sesión como un servicio  
  
 Si especifica 0 (Windows), debe establecer el valor de la propiedad [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) en una cuenta de usuario de Windows válida correspondiente.  
  
 Si especifica 1 (SQL Server), asegúrese de que el valor de [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) se corresponda con un inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] válido.  
  
 Si especifica 2 (servicio de Windows), el servidor de informes usará una cuenta de [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] y la cuenta de servicio de Windows para tener acceso a la base de datos del servidor de informes. Se omite la propiedad DatabaseLogonAccount.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Miembros MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
