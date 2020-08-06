---
title: Método GenerateDatabaseCreationScript (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseCreationScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseCreationScript method
ms.assetid: 25232dc7-00fe-4cd1-8a1c-7e36d552de00
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5e798aa25bec1cc478a6ec2cbdd0c21f44fa8215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87671913"
---
# <a name="generatedatabasecreationscript-method-wmi-msreportserver_configurationsetting"></a>Método GenerateDatabaseCreationScript (MSReportServer_ConfigurationSetting de WMI)
  Genera un script SQL que se puede utilizar para crear una base de datos del servidor de informes.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub GenerateDatabaseCreationScript(ByVal DatabaseName As String, _  
    ByVal Lcid As Int32, ByVal IsSharePointMode As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseCreationScript(string DatabaseName, Int32 Lcid,   
    Boolean IsSharePointMode, out string Script, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parámetros  
 *Databasename*  
 Cadena que contiene el nombre de la base de datos del servidor de informes que se va a crear.  
  
 *Lcid*  
 Valor usado para la localización de nombres de roles.  
  
 *IsSharePointMode*  
 Indica si se desea crear la base de datos en modo nativo o en modo de SharePoint.  
  
> [!IMPORTANT]  
>  A partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , *IsSharePointMode* = `True` no se admite porque en modo de SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] es un servicio compartido de SharePoint y no está controlado por el proveedor WMI. Este parámetro siempre debe establecerse en `False`.  
  
 *Script*  
 [out] Cadena que contiene el script SQL generado.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente. Un valor distinto de cero indica que se ha producido un error.  
  
## <a name="remarks"></a>Observaciones  
 Este método genera un script SQL que crea bases de datos del servidor de informes para la versión del servidor de informes al que se está conectado actualmente.  
  
 El valor proporcionado en el parámetro *DatabaseName* debe cumplir las convenciones de nomenclatura de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 El método no comprueba la existencia de la base de datos al generar el script.  
  
 Este método no comprueba la existencia de la base de datos del servidor de informes al generar el script.  
  
 El script generado admite [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 y [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Consulte también  
 [Miembros MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
