---
title: Método RemoveURL (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RemoveURL method
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a32989e8ce8986b785e829d8cc7fcf58fbbf240
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674004"
---
# <a name="removeurl-method-wmi-msreportserver_configurationsetting"></a><span data-ttu-id="09365-102">Método RemoveURL (MSReportServer_ConfigurationSetting de WMI)</span><span class="sxs-lookup"><span data-stu-id="09365-102">RemoveURL Method (WMI MSReportServer_ConfigurationSetting)</span></span>
  <span data-ttu-id="09365-103">Quita una dirección URL reservada para el servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="09365-103">Removes a URL reserved for the report server.</span></span> <span data-ttu-id="09365-104">Si es necesario quitar varias direcciones URL, esta operación debe realizarse una a una llamando a esta API.</span><span class="sxs-lookup"><span data-stu-id="09365-104">If there are multiple URLs that need to be removed, this must be done one by one calling this API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09365-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="09365-105">Syntax</span></span>  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09365-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="09365-106">Parameters</span></span>  
 <span data-ttu-id="09365-107">*Aplicación*</span><span class="sxs-lookup"><span data-stu-id="09365-107">*Application*</span></span>  
 <span data-ttu-id="09365-108">Nombre de la aplicación para la que se quita la reserva.</span><span class="sxs-lookup"><span data-stu-id="09365-108">The name of application for which to remove the reservation.</span></span>  
  
 <span data-ttu-id="09365-109">*URLString*</span><span class="sxs-lookup"><span data-stu-id="09365-109">*URLString*</span></span>  
 <span data-ttu-id="09365-110">Dirección URL para la reserva.</span><span class="sxs-lookup"><span data-stu-id="09365-110">The URL for the reservation.</span></span>  
  
 <span data-ttu-id="09365-111">*lcid*</span><span class="sxs-lookup"><span data-stu-id="09365-111">*lcid*</span></span>  
 <span data-ttu-id="09365-112">Configuración regional que se utilizará para los mensajes de error devueltos.</span><span class="sxs-lookup"><span data-stu-id="09365-112">The locale to use for the error messages returned.</span></span>  
  
 <span data-ttu-id="09365-113">*Error*</span><span class="sxs-lookup"><span data-stu-id="09365-113">*Error*</span></span>  
 <span data-ttu-id="09365-114">[out] Descripción del error que se produjo.</span><span class="sxs-lookup"><span data-stu-id="09365-114">[out] The description of the error that occurred.</span></span>  
  
 <span data-ttu-id="09365-115">*HRESULT*</span><span class="sxs-lookup"><span data-stu-id="09365-115">*HRESULT*</span></span>  
 <span data-ttu-id="09365-116">[out] Valor que indica si la llamada se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="09365-116">[out] Value indicating whether the call succeeded or failed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09365-117">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="09365-117">Return Value</span></span>  
 <span data-ttu-id="09365-118">Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="09365-118">Returns an *HRESULT* indicating success or failure of the method call.</span></span> <span data-ttu-id="09365-119">Un valor de 0 indica que la llamada al método se realizó correctamente; un código de error indica que la llamada no se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="09365-119">A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09365-120">Observaciones</span><span class="sxs-lookup"><span data-stu-id="09365-120">Remarks</span></span>  
 <span data-ttu-id="09365-121">*UrlString* no incluye el nombre del directorio virtual: el [Método SetVirtualDirectory &#40;MSReportServer_ConfigurationSetting de WMI&#41;](configurationsetting-method-setvirtualdirectory.md) se proporciona para ese propósito.</span><span class="sxs-lookup"><span data-stu-id="09365-121">*UrlString* does not include the Virtual Directory name - the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method is provided for that purpose.</span></span>  
  
 <span data-ttu-id="09365-122">Antes de llamar al método [ReserveURL](configurationsetting-method-reserveurl.md) , debe proporcionar un valor para la propiedad de configuración VirtualDirectory en el parámetro *Application* .</span><span class="sxs-lookup"><span data-stu-id="09365-122">Before calling the [ReserveURL](configurationsetting-method-reserveurl.md) method, you must supply a value for the VirtualDirectory configuration property for the *Application* parameter.</span></span> <span data-ttu-id="09365-123">Use el [Método SetVirtualDirectory &#40;MSReportServer_ConfigurationSetting de WMI&#41;](configurationsetting-method-setvirtualdirectory.md) para establecer la propiedad VirtualDirectory.</span><span class="sxs-lookup"><span data-stu-id="09365-123">Use the [SetVirtualDirectory Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md) method to set the VirtualDirectory property.</span></span>  
  
 <span data-ttu-id="09365-124">Si [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ha proporcionado un certificado SSL y ninguna otra dirección URL lo necesita, se quita.</span><span class="sxs-lookup"><span data-stu-id="09365-124">If an SSL Certificate was provisioned by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and no other URLs need it, it is removed.</span></span>  
  
 <span data-ttu-id="09365-125">Este método hace que todos los dominios de aplicación sin configuración sean objeto de reciclaje con reinicio de dominios de aplicación y se detengan durante esta operación; los dominios de aplicación se reinician una vez completada la operación.</span><span class="sxs-lookup"><span data-stu-id="09365-125">This method causes all non-configuration app domains to hard recycle and stop during this operation; app domains are restarted after this operation complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09365-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09365-126">Requirements</span></span>  
 <span data-ttu-id="09365-127">**Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09365-127">**Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09365-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="09365-128">See Also</span></span>  
 [<span data-ttu-id="09365-129">Miembros MSReportServer_ConfigurationSetting</span><span class="sxs-lookup"><span data-stu-id="09365-129">MSReportServer_ConfigurationSetting Members</span></span>](msreportserver-configurationsetting-members.md)  
  
  