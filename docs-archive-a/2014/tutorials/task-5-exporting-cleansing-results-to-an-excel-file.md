---
title: 'Tarea 5: exportar los resultados de la limpieza a un archivo de Excel | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0dbdc1bef348e03e211e4933132985ea2c089b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675690"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a>Tarea 5: Exportación de los resultados de la limpieza a un archivo de Excel
  En esta tarea, exportará los resultados de la actividad de limpieza a un archivo de Excel. Vea el tema sobre la [fase de exportación](https://msdn.microsoft.com/library/hh213061.aspx#Export) para obtener más detalles.  
  
1.  En el panel derecho, seleccione **Excel** para el **tipo de destino**.  
  
2.  Haga clic en **examinar**, especifique el nombre del archivo de salida como **proveedor con limpieza List.xls**y, a continuación, haga clic en **abrir**.  
  
3.  Seleccione **solo datos** para que el formato de **salida** exporte solo los datos limpios. La segunda opción, **datos y limpieza**, le permite exportar detalles de la actividad de limpieza junto con los datos limpios. La opción de **formato normalizar** permite aplicar los formatos de salida definidos en un dominio a los valores de ese dominio. En el tutorial no ha definido ningún formato de salida en ningún dominio.  
  
     ![Exportar página de resultados de limpieza](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Exportar página de resultados de limpieza")  
  
4.  Haga clic en **exportar** para exportar los datos. No haga clic en **Finalizar** todavía.  
  
5.  Haga clic en **cerrar** en el cuadro de diálogo **exportación** .  
  
6.  Haga clic en **Finalizar** para finalizar la actividad. Si olvidó exportar los resultados antes de hacer clic en **Finalizar**, haga clic en **Abrir proyecto de calidad de datos** en la Página principal del **cliente DQS**, seleccione **limpiar lista de proveedores** en la lista de proyectos y haga clic en **siguiente** en la parte inferior de la pantalla para volver a la fase de **exportación** del proceso de limpieza. También puede cambiar a la pestaña **administrar y ver resultados** haciendo clic en el botón **atrás** .  
  
7.  Abra el **List.xlsdel proveedor limpio** y haga lo siguiente:  
  
    1.  Asegúrese de que no haya direcciones de correo electrónico que terminen con adventure-work.com (sin el carácter ') buscando adventure-work.com en la hoja de cálculo.  
  
    2.  Compruebe que no hay ningún valor de **Estados Unidos** en la columna **país** .  
  
    3.  Busque **Los Angeles** y compruebe que el valor de **State** está establecido en **CA**.  
  
    4.  Confirme que no hay términos **Co.**, **Corp.** y **Inc.**.  
  
    5.  Elimine la columna **validación de direcciones** de la hoja de cálculo y guarde el archivo de Excel. Esta columna adicional corresponde al dominio de compuesto Validación de direcciones.  
  
## <a name="next-step"></a>siguiente paso  
 [Tarea 6: Importación de valores del proyecto Limpiar lista de proveedores](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
