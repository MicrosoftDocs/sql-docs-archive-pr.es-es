---
title: Seleccionar calendarios (Asistente para dimensiones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.serverSpecialCalendars.f1
ms.assetid: 6e28a020-2586-4b13-9333-b499fb1b33af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2048ee20dd91c942f01982d02f3265a6bad670dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673917"
---
# <a name="select-calendars-dimension-wizard"></a>Seleccionar calendarios (Asistente para dimensiones)
  Use la página **Seleccionar calendarios** para crear jerarquías adicionales que representan calendarios fiscales, de generación de informes, de fabricación o International Standards Organization (ISO) 8601 para la dimensión de tiempo.  
  
> [!NOTE]  
>   Esta página se muestra solo si se ha seleccionado la opción **Dimensión de tiempo de servidor** en la página **Seleccionar el tipo de dimensión** o se ha seleccionado la opción **Generar la dimensión sin un origen de datos** en la página **Seleccionar método de generación** y se ha seleccionado **Dimensión de tiempo** en la página **Seleccionar el tipo de dimensión** .  
  
## <a name="options"></a>Opciones  
 **Calendario fiscal**  
 Seleccione esta opción para crear una jerarquía de tiempo basada en un calendario fiscal.  
  
 **Día y mes de inicio**  
 Seleccione el día y el mes en el que comienza el calendario fiscal.  
  
> [!NOTE]  
>   Esta opción solo está disponible si se ha seleccionado **Calendario fiscal** .  
  
 **Convención de nomenclatura del año fiscal**  
 Seleccione la convención de nomenclatura usada por el calendario fiscal. Seleccione **Nombre del año natural** o **Nombre del año natural +1**.  
  
> [!NOTE]  
>   Esta opción solo está disponible si se ha seleccionado **Calendario fiscal** .  
  
 **Calendario de informe (o marketing)**  
 Seleccione esta opción para crear una jerarquía de tiempo basada en un calendario de informe.  
  
 **Semana y mes de inicio**  
 Seleccione la semana y el mes en que comienza el calendario de informe.  
  
> [!NOTE]  
>  Esta opción solo está disponible si se ha seleccionado **Calendario de informe (o marketing)** .  
  
 **Semana por patrón mensual**  
 Seleccione la semana por patrón mensual usada por el calendario de informe.  
  
> [!NOTE]  
>  Esta opción solo está disponible si se ha seleccionado **Calendario de informe (o marketing)** .  
  
 En la tabla siguiente se enumeran las opciones disponibles para la semana por patrón mensual.  
  
|Value|Descripción|  
|-----------|-----------------|  
|**Week 445**|El primer mes del trimestre tiene 4 semanas, el segundo mes tiene 4 semanas y el tercero tiene 5 semanas.|  
|**Week 454**|El primer mes del trimestre tiene 4 semanas, el segundo mes tiene 5 semanas y el tercero tiene 4 semanas.|  
|**Semana 544**|El primer mes del trimestre tiene 5 semanas, el segundo mes tiene 4 semanas y el tercero tiene 4 semanas.|  
  
 **Calendario de fabricación**  
 Seleccione esta opción para crear una jerarquía de tiempo basada en un calendario de fabricación.  
  
 **Semana y mes de inicio**  
 Seleccione la semana y el mes en que comienza el calendario de fabricación.  
  
> [!NOTE]  
>   Esta opción solo está disponible cuando si se ha seleccionado **Calendario de fabricación** .  
  
 **Trimestre con períodos adicionales**  
 Seleccione o escriba el trimestre que contendrá los periodos adicionales.  
  
> [!NOTE]  
>   Esta opción solo está disponible cuando si se ha seleccionado **Calendario de fabricación** .  
  
 **Calendario ISO 8601**  
 Seleccione esta opción para crear una jerarquía de tiempo basada en el calendario ISO 8601.  
  
## <a name="see-also"></a>Consulte también  
 [Asistente para dimensiones (ayuda F1)](dimension-wizard-f1-help.md)   
 [Dimensiones &#40;Analysis Services de datos multidimensionales&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensiones en modelos multidimensionales](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
