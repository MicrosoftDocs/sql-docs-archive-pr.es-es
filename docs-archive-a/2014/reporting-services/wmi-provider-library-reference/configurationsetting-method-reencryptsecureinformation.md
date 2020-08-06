---
title: Método ReencryptSecureInformation (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1a0c657b69d624df8895ae4d5a6d12277b011b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675195"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserver_configurationsetting"></a>Método ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting)
  Genera una nueva clave de cifrado y vuelve a cifrar toda la información segura en el catálogo utilizando esta nueva clave.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parámetros  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
 *ExtendedErrors[]*  
 [out] Matriz de cadenas que contiene los errores adicionales devueltos por la llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente. Un valor distinto de cero indica que se ha producido un error.  
  
## <a name="remarks"></a>Observaciones  
 El método ReencryptSecureInformation permite que el administrador reemplace la clave de cifrado existente por una nueva clave.  
  
 Cuando se invoca este método, el servidor de informes genera una nueva clave de cifrado y la utiliza en todo el contenido cifrado para volver a cifrarlo.  
  
 Las extensiones de entrega pueden almacenar la información segura en sus estructuras de configuración de entrega. Cuando se llama a ReencryptSecureInformation, el servidor de informes carga cada suscripción y la extensión de entrega correspondiente para volver a cifrar la información almacenada en la configuración asociada.  
  
 Si este método se ejecuta en un equipo en una implementación escalada, cada equipo en la implementación escalada deberá inicializarse de nuevo.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Miembros MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
