---
title: Método BackupEncryptionKey (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- BackupEncryptionKey method
ms.assetid: da1d5dae-2517-448e-96fb-5379c93222ea
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d625401324e2117ee1e9677d840854fa7b63c6e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748586"
---
# <a name="backupencryptionkey-method-wmi-msreportserver_configurationsetting"></a>Método BackupEncryptionKey (WMI MSReportServer_ConfigurationSetting)
  Realiza una copia de seguridad de la clave de cifrado de la instancia del servidor de informes especificada. La clave de cifrado se almacena cifrada con una contraseña.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub BackupEncryptionKey(Password as String, _  
    ByRef KeyFile() as Integer, ByRef Length as Int32, _  
    ByRef HRESULT as Int32, ByRef ExtendedErrors() as String)  
  
```  
  
```csharp  
public void BackupEncryptionKey(string Password, out Byte[] KeyFile,   
    out Int32 Length, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parámetros  
 *Contraseña*  
 Cadena utilizada para cifrar la clave de cifrado antes de devolverse.  
  
 *KeyFile[]*  
 [out] Matriz que contiene la clave de cifrado cifrada.  
  
 *Longitud*  
 [out] Longitud de la matriz devuelta por el método.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
 *ExtendedErrors[]*  
 [out] Matriz de cadenas que contiene los errores adicionales devueltos por la llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente. Un valor distinto de cero indica que se ha producido un error.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Miembros MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
