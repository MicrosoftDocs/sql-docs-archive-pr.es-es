---
title: Método SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 15d1b7fa5fc6d69a963785cdaf976c80623c47f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748558"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a>Método SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting)
  Ejecuta el servicio de Windows de servidor de informes como el usuario de Windows especificado y concede a esta cuenta suficientes permisos de sistema de archivos para permitir que servidor de informes funcione.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parámetros  
 *UseBuiltInAccount*  
 Indica si la cuenta especificada es una cuenta de Windows integrada.  
  
 *Cuenta*  
 La cuenta de Windows que se utilizará para ejecutar el servicio de Windows, en formato "DOMAIN\alias."  
  
 *Contraseña*  
 La contraseña de la cuenta.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente. Un valor distinto de cero indica que se ha producido un error.  
  
## <a name="remarks"></a>Observaciones  
 Cuando el parámetro *UseBuiltInAccount* se establece en `true` y el servidor de informes se ejecuta en [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] Microsoft o Windows XP, el valor de los parámetros *Name*, *Domain*y *password* se omite y se usa la cuenta de sistema local.  
  
 Cuando el parámetro *UseBuiltInAccount* se establece en `true` y el servidor de informes se ejecuta en Windows Server 2003, las propiedades de *dominio* y *contraseña* se omiten y el campo de nombre debe contener "builtin\system" o "," o "Builtin\LocalService".  
  
 El método SetWindowsServiceIdentity establece los permisos de archivo en los archivos y carpetas en el directorio de instalación del servidor de informes.  
  
 La cuenta especificada en el parámetro *account* requiere `LogonAsService` derechos en Windows. El método permite este derecho a la cuenta especificada.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Miembros MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
