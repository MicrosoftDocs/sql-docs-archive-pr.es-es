---
title: Tabla de errores de SoapException | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- SoapException class
ms.assetid: 3dbf1b5a-bd2a-4385-925d-5d095d72014c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b17ecc3049ce1afe07f3aa2e0b06f417d4f8dcee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676336"
---
# <a name="soapexception-errors-table"></a>Tabla de errores de SoapException
  El servidor de informes genera errores y mensajes de error en la excepción SOAP según los errores que se producen en [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. En la tabla siguiente se muestran los errores que son accesibles desde métodos a través de un elemento **SoapException** en el servicio web del servidor de informes. Se organiza según el método o métodos que inician la excepción.  
  
|Métodos|Código de error|  
|-----------------|----------------|  
|**ALL**|**rsEvaluationCopyExpired**|  
|**ALL**|**rsFailedToDecryptConfigInformation**|  
|**ALL**|**rsInvalidRSEditionConfiguration**|  
|**ALL**|**rsReportServerNotActivated**|  
|**ALL**|**rsServerBusy**|  
|**ALL**|**rsReportServerServiceUnavailable**|  
|**ALL**|**rsReportServerDisabled**|  
|**ALL** excepto **GetPermissions**, **GetRenderResource**, **GetSystemPermissions**, **ListEvents** y **ListSecureMethods**|**rsAccessDenied**|  
|**ALL** excepto **CreateBatch**, **ExecuteBatch**, **GetSystemPolicies**, **GetSystemPermissions**, **GetSystemProperties**, **ListEvents**, **ListJobs**, **ListRoles**, **ListSchedules**, **ListSecureMethods**, **ListSubscriptions**, **ListSystemRoles**, **ListSystemTasks** y **ListTasks**|**rsMissingParameter**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource**, **CreateSubscription**, **DeleteItem**, **DeleteReportHistorySnapshot**, **DisableDataSource**, **EnableDataSource**, **FindItems**, **FlushCache**, **GetCacheOptions**, **GetDataSourceContents**, **GetExecutionOptions**, **GetPermissions**, **GetPolicies**, **GetProperties**, **GetReportDataSourcePrompts**, **GetReportDataSources**, **GetReportDefinition**, **GetReportHistoryLimit**, **GetReportHistoryOptions**, **GetReportLink**, **GetReportParameters**, **GetResourceContents**, **GetRoleProperties**, **GetServerDateTime**, **IheritParentSecurity**, **ListChildren**, **ListLinkedReports**, **ListReportHistory**, **ListReportsUsingDataSource**, **ListSchedules**, **ListSubscriptions**, **ListSubscriptionsUsingDataSource**, **MoveItem**, **Render**, **RenderStream**, **SetCacheOptions**, **SetDataSourceContents**, **SetExecutionOptions**, **SetPolicies**, **SetProperties**, **SetReportDataSources**, **SetReportDefinition**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **UpdateReportExecutionSnapshot** y **ValidateExtensionSettings**|**rsItemNotFound**|  
|**CancelBatch**, **CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource**, **CreateRole**, **CreateSchedule**, **CreateSubscription**, **DeleteItem**, **DeleteReportHistorySnapshot**, **DeleteRole**, **DeleteSchedule**, **DeleteSubscription**, **DisableDataSource**, **EnableDataSource**, **ExecuteBatch**, **FindItems**, **FlushCache**, **GetResourceContents**, **GetServerDateTime**, **MoveItem**, **PauseSchedule**, **ResumeSchedule**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetExecutionOptions**, **SetPolicies**, **SetProperties**, **SetReportDataSources**, **SetReportDefinition**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **SetRoleProperties**, **SetScheduleProperties**, **SetSubscriptionProperties**, **SetSystemPolicies**, **SetSystemProperties**, **UpdateReportExecutionSnapshot** y **ValidateExtensionSettings**|**rsBatchNotFound**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource**, **CreateSubscription**, **DeleteItem**, **DeleteReportHistorySnapshot**, **DisableDataSource**, **EnableDataSource**, **FindItems**, **FlushCache**, **GetCacheOptions**, **GetDataSourceContents**, **GetExecutionOptions**, **GetItemType**, **GetPermissions**, **GetPolicies**, **GetProperties**, **GetReportDataSourcePrompts**, **GetReportDataSources**, **GetReportDefinition**, **GetReportHistoryLimit**, **GetReportHistoryOptions**, **GetReportLink**, **GetResourceContents**, **GetServerDateTime**, **IheritParentSecurity**, **ListChildren**, **ListLinkedReports**, **ListReportHistory**, **ListSchedules**, **ListSubscriptionsUsingDataSource**, **MoveItem**, **Render**, **RenderStream**, **SetCacheOptions**, **SetDataSourceContents**, **SetExecutionOptions**, **SetPolicies**, **SetProperties**, **SetReportDataSources**, **SetReportDefinition**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **SetSubscriptionProperties**, **UpdateReportExecutionSnapshot** y **ValidateExtensionSettings**|**rsInvalidItemPath**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateReportHistorySnapshot**, **CreateResource**, **CreateSubscription**, **DeleteReportHistorySnapshot**, **DisableDataSource**, **EnableDataSource**, **FindItems**, **FlushCache**, **GetCacheOptions**, **GetDataSourceContents**, **GetExecutionOptions**, **GetReportDataSourcePrompts**, **GetReportDataSources**, **GetReportDefinition**, **GetReportHistoryLimit**, **GetReportHistoryOptions**, **GetReportLink**, **GetReportParameters**, **GetResourceContents**, **GetServerDateTime**, **GetSystemProperties**, **ListChildren**, **ListLinkedReports**, **ListReportHistory**, **ListReportsUsingDataSource**, **ListSchedules**, **ListSubscriptions**, **ListSubscriptionsUsingDataSource**, **MoveItem**, **Render**, **RenderStream**, **SetCacheOptions**, **SetDataSourceContents**, **SetExecutionOptions**, **SetReportDataSources**, **SetReportDefinition**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetReportLink**, **SetReportParameters**, **SetResourceContents**, **UpdateReportExecutionSnapshot** y **ValidateExtensionSettings**|**rsWrongItemType**|  
|**CreateReport**, **CreateResource**, **DeleteReportHistorySnapshot**, **DeleteSchedule**, **DeleteSubscription**, **GetDataDrivenSubscriptionProperties**, **GetSubscriptionProperties**, **ListChildren**, **ListScheduledReports**, **PauseSchedule**, **Render**, **RenderStream**, **ResumeSchedule**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetReportHistoryLimit**, **SetReportHistoryOptions**, **SetScheduleProperties** y **SetSubscriptionProperties**|**rsParameterTypeMismatch**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateSchedule**, **CreateSubscription**, **FindItems**, **GetReportParameters**, **PrepareQuery**, **Render**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetPolicies**, **SetReportDataSources**, **SetReportParameters**, **SetScheduleProperties**, **SetSubscriptionProperties** y **SetSystemPolicies**|**rsMissingElement**|  
|**CreateDataDrivenSubscription**, **CreateDataSource**, **CreateSchedule**, **CreateSubscription**, **PrepareQuery**, **Render**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetProperties**, **SetReportDataSources**, **SetReportParameters**, **SetScheduleProperties**, **SetSubscriptionProperties** y **SetSystemProperties**|**rsInvalidElement**|  
|**CreateDataDrivenSubscription**, **CreateSchedule**, **CreateSubscription**, **FindItems**, **GetRenderResource**, **PrepareQuery**, **Render**, **RenderStream**, **SetCacheOptions**, **SetDataDrivenSubscriptionProperties**, **SetExecutionOptions**, **SetProperties**, **SetReportHistoryOptions**, **SetReportParameters**, **SetScheduleProperties**, **SetSubscriptionProperties** y **SetSystemProperties**|**rsElementTypeMismatch**|  
|**CreateDataSource**, **CreateRole**, **GetDataDrivenSubscriptionProperties**, **GetRenderResource**, **ListExtensions**, **Render**, **SetDataDrivenSubscriptionProperties**, **SetDataSourceContents**, **SetExecutionOptions**, **SetReportHistoryLimit**, **SetReportHistoryOptions** y **SetScheduleProperties**|**rsInvalidParameter**|  
|**CreateDataDrivenSubscription**, **CreateReportHistorySnapshot**, **CreateSubscription**, **PrepareQuery**, **SetDataDrivenSubscriptionProperties**, **SetExecutionOptions**, **SetReportHistoryOptions** y **SetSubscriptionProperties**|**rsInvalidDataSourceCredentialSetting**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateReportHistorySnapshot**, **CreateSchedule**, **CreateSubscription**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**, **UpdateReportExecutionSnapshot**|**rsReportParameterValueNotSet**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **GetExtensionSettings**, **GetRenderResource**, **Render**, **RenderStream**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsMultipleExtensionsFoundInAssembly**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateSubscription**, **Render**, **SetCacheOptions**, **SetExecutionOptions**, **SetReportParameters**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsReportParameterTypeMismatch**|  
|**CreateSchedule**, **CreateSubscription**, **DeleteSchedule**, **PauseSchedule**, **ResumeSchedule**, **SetCacheOptions**, **SetExecutionOptions**, **SetScheduleProperties** y **SetSubscriptionProperties**|**rsSchedulerNotResponding**|  
|**DeleteSchedule**, **GetScheduleProperties**, **ListScheduledReports**, **PauseSchedule**, **ResumeSchedule**, **SetCacheOptions**, **SetExecutionOptions** y **SetScheduleProperties**|**rsScheduleNotFound**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateSubscription**, **Render**, **SetReportParameters**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsReadOnlyReportParameter**|  
|**CreateDataDrivenSubscriptionProperties**, **CreateSubscription**, **GetReportParameters**, **Render**, **SetReportParameters**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsUnknownReportParameter**|  
|**DeleteSubscription**, **GetDataDrivenSubscriptionProperties**, **GetSubscriptionProperties**, **SetDataDrivenSubscriptionProperties** y **SetExecutionOptions**, **SetSubscriptionProperties**|**rsSubscriptionNotFound**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **GetExtensionSettings**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsDeliveryExtensionNotFound**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **GetExtensionSettings**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsDeliveryError**|  
|**CreateDataDrivenSubscription**, **GetDataDrivenSubscriptionProperties**, **PrepareQuery** y **SetDataDrivenSubscriptionProperties**|**rsSecureConnectionRequired**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsCannotSubscribeToEvent**|  
|**CreateDataDrivenSubscription**, **CreateSubscription**, **FireEvent**, **SetDataDrivenSubscriptionProperties** y **SetSubscriptionProperties**|**rsUnknownEventType**|  
|**CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateResource** y **MoveItem**|**rsItemPathLengthExceeded**|  
|**CopyItem**, **CreateFolder**, **CreateReport** y **CreateResource**, **DeleteItem**|**rsReservedItem**|  
|**CreateDataSource**, **SetDataSourceContents** y **SetReportDataSources**|**rsInvalidElementCombination**|  
|**SetCacheOptions**, **SetExecutionOptions** y **SetReportHistoryOptions**|**rsInvalidParameterCombination**|  
|**CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateResource** y **MoveItem**|**rsInvalidItemName**|  
|**CreateDataSource**, **CreateFolder**, **CreateLinkedReport**, **CreateReport**, **CreateResource** y **MoveItem**|**rsItemAlreadyExists**|  
|**CreateFolder**, **CreateLinkedReport**, **CreateReport** y **CreateResource**, **SetProperties**|**rsReadOnlyProperty**|  
|**GetPolicies**, **GetSystemPolicies**, **SetPolicies** y **SetSystemPolicies**|**rsInvalidPolicyDefinition**|  
|**SetCacheOptions**, **SetDataSourceContents**, **SetReportDataSources** y **SetReportParameters**|**rsOperationPreventsUnattendedExecution**|  
|**CreateReportHistorySnapshot**, **Render**, **PrepareQuery** y **UpdateReportExecutionSnapshot**|**rsInvalidDataSourceReference**|  
|**CreateReportHistorySnapshot**, **PrepareQuery**, **Render** y **UpdateReportExecutionSnapshot**|**rsDataSourceDisabled**|  
|**CreateReport**, **PrepareQuery** y **SetReportDefinition**|**rsProcessingError**|  
|**GetRenderResource**, **Render** y **RenderStream**|**rsInvalidReportLink**|  
|**DeleteReportHistorySnapshot**, **Render** y **RenderStream**|**rsReportHistoryNotFound**|  
|**SetCacheOptions**, **SetExecutionOptions** y **SetReportHistoryOptions**|**rsReportMayNotBeScheduled**|  
|**CreateDataDrivenSubscription**, **GetDataDrivenSubscriptionProperties** y **SetDataDrivenSubscriptionProperties**|**rsOperationNotSupported**|  
|**CreateDataSource**, **SetDataSourceContents** y **SetReportDataSources**|**rsDataExtensionNotFound**|  
|**DeleteRole**, **SetPolicies** y **SetRoleProperties**|**rsRoleNotFound**|  
|**DeleteReportHistorySnapshot**, **Render** y **RenderStream**|**rsParametersNotSpecified**|  
|**GetReportParameters** y **SetReportParameters**|**rsNotSupported**|  
|**SetReportParameters** y **UpdateReportExecutionSnapshot**|**rsReportSnapshotNotEnabled**|  
|**CreateSchedule** y **SetScheduleProperties**|**rsScheduleAlreadyExists**|  
|**CreateRole** y **SetRoleProperties**|**rsTaskNotFound**|  
|**CreateRole** y **SetRoleProperties**|**rsMixedTasks**|  
|**ListSubscriptions** y **SetPolicies**|**rsUnknownUserName**|  
|**MoveItem**|**rsInvalidMove**|  
|**RenderStream**|**rsStreamNotFound**|  
|**RenderStream**|**rsMissingSessionId**|  
|**Representar**|**rsReportNotReady**|  
|**Representar**|**rsAssemblyNotPermissioned**|  
|**SetExecutionOptions**|**rsReportSnapshotEnabled**|  
|**FindItems**|**rsInvalidSearchOperator**|  
|**SetReportDataSources**|**rsDataSourceNotFound**|  
|**PrepareQuery** y **Render**|**rsDataSourceNoPrompt**|  
|**PrepareQuery**|**rsCannotPrepareQuery**|  
|**DeleteRole**|**rsReservedRole**|  
|**CreateRole**|**rsEmptyRole**|  
|**InheritParentSecurity**|**rsInheritedPolicy**|  
|**CreateRole**|**rsRoleAlreadyExists**|  
|**InheritParentSecurity**|**rsCannotDeleteRootPolicy**|  
|**CancelJob**|**rsJobWasCanceled**|  
|**ListSecureMethods**|**rsServerConfigurationError**|  
  
## <a name="see-also"></a>Consulte también  
 [Introducción al control de excepciones en Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Referencia de errores y eventos &#40;Reporting Services&#41;](../../troubleshooting/errors-and-events-reference-reporting-services.md)   
 [Reporting Services (clase SoapException)](reporting-services-soapexception-class.md)   
 [Usar la propiedad Detail para administrar errores concretos](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
