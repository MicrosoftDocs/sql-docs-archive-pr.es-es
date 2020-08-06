---
title: Validar datos (complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f8e97ff6481996b2e16436e1f78478bd234fe6ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673074"
---
# <a name="validating-data-mds-add-in-for-excel"></a>Validar datos (complemento MDS para Excel)
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], al publicar datos, tienen lugar dos tipos de validación:  
  
-   Las reglas de negocio definidas se aplican a los datos.  
  
-   Los datos se comparan con los valores de atributo permitido (por ejemplo, el número de caracteres o el tipo de datos).  
  
 En cada caso, los datos se publican en el repositorio MDS. Los datos que no son válidos se resaltan y los detalles de error se pueden mostrar en las columnas de estado.  
  
## <a name="when-validation-occurs"></a>Cuándo se produce la validación  
 En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], la validación tiene lugar al publicar datos nuevos o modificados, o cuando las reglas de negocios se aplican manualmente.  
  
 Cuando las reglas de negocios producen un error, los datos siguen publicándose en el repositorio MDS. Cuando se produce un error en la validación de entrada, los datos no se publican en el repositorio.  
  
## <a name="validation-statuses"></a>Estados de validación  
 En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], son posibles los siguientes estados de validación.  
  
|Estado|Descripción|  
|------------|-----------------|  
|Error|Uno o más valores de la fila no pudieron realizar la validación con las reglas de negocios definidas por un administrador MDS.|  
|No se validaron|Los valores de la fila aún no se han validado con las reglas de negocios.|  
|Correcto|Todos los valores de la fila han pasado la validación según las reglas de negocios.|  
  
## <a name="input-statuses"></a>Estados de entrada  
 En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], son posibles los siguientes estados de entrada.  
  
|Estado|Descripción|  
|------------|-----------------|  
|Error|Uno o más valores de la fila no cumplen los requisitos del sistema como la longitud o el tipo de datos. El valor no se actualiza en el repositorio MDS.|  
|Nueva fila|Los valores de la fila aún no se han publicado en el repositorio MDS.|  
|Solo lectura|El usuario que ha iniciado sesión tiene permisos de solo lectura en uno o varios valores de fila y los valores no pueden actualizarse.|  
|Sin cambios|No se ha cambiado ningún valor de la fila en la hoja de cálculo. Esto no significa que los valores del repositorio no hayan cambiado; para obtener los datos más recientes de la hoja, en el grupo **Conectar y cargar** , haga clic en **Cargar o actualizar**.<br /><br /> Esta es la configuración predeterminada de cada fila.|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Determine qué valores no pasan las reglas de negocios definidas.|[Aplicar reglas de negocios &#40;complemento MDS para Excel&#41;](apply-business-rules-mds-add-in-for-excel.md)|  
|Para ayudar a corregir los errores de validación, vea todas las transacciones que han tenido lugar para un miembro.|[Ver todas las anotaciones o transacciones de un miembro &#40;complemento MDS para Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
  
-   [Complemento MDS para Excel de &#40;de datos de publicación&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
