---
title: Analizar un modelo tabular en Excel (SSAS tabular) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
author: minewiskan
ms.author: owend
ms.openlocfilehash: fae542ffb5b470d23d9cf27fcc11367f571e7cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675522"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a>Analizar un modelo tabular en Excel (SSAS tabular)
  La característica Analizar en Excel de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] abre Microsoft Excel, crea una conexión de origen de datos con la base de datos del área de trabajo del modelo y agrega una tabla dinámica a la hoja de cálculo. Los objetos del modelo (tablas, columnas, medidas, jerarquías y KPI) se incluyen como campos en la lista de campos de la tabla dinámica.  
  
> [!NOTE]  
>  Para usar la característica Analizar en Excel, tiene que tener instalado Microsoft Office 2003 o posterior en el mismo equipo que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Si Office no está instalado en el mismo equipo, puede usar Excel en otro equipo y conectarse a la base de datos del área de trabajo del modelo como un origen de datos. A continuación, podrá agregar manualmente una tabla dinámica a la hoja de cálculo. Los objetos del modelo (tablas, columnas, medidas y KPI) se incluyen como campos en la lista de campos de la tabla dinámica.  
  
## <a name="tasks"></a>Tareas  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>Para analizar un proyecto de modelo tabular mediante la característica Analizar en Excel  
  
1.  En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y después en **Analizar en Excel**.  
  
2.  En el cuadro de diálogo **Elegir credenciales y perspectivas** , seleccione una de las opciones de credenciales siguientes para conectarse al origen de datos del área de trabajo del modelo:  
  
    -   Para usar la cuenta de usuario actual, seleccione **Usuario de Windows actual**.  
  
    -   Para usar una cuenta de usuario diferente, seleccione **Otro usuario de Windows**.  
  
         Normalmente, esta cuenta de usuario será un miembro de un rol. No se requiere una contraseña. La cuenta solo se puede utilizar en el contexto de una conexión de Excel a la base de datos del área de trabajo.  
  
    -   Para usar un rol de seguridad, seleccione **Rol**y, a continuación, en el cuadro de lista, seleccione uno o varios roles.  
  
         Los roles de seguridad se deben definir mediante el Administrador de roles. Para obtener más información, vea [Crear y administrar roles &#40;SSAS tabular&#41;](roles-ssas-tabular.md).  
  
3.  Para usar una perspectiva, seleccione una en el cuadro de lista **Perspectiva** .  
  
     Las perspectivas (distintas de las predeterminadas) se deben definir mediante el cuadro de diálogo Perspectivas. Para obtener más información, vea [crear y administrar perspectivas &#40;&#41;tabular de SSAS ](perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  La lista de campos de tabla dinámica de Excel no se actualiza automáticamente a medida que se realizan cambios en el proyecto de modelos en el diseñador de modelos. Para actualizar dicha lista, en Excel, haga clic en **Actualizar** en la cinta **Opciones**.  
  
## <a name="see-also"></a>Consulte también  
 [Analizar en Excel &#40;SSAS tabular&#41;](analyze-in-excel-ssas-tabular.md)  
  
  
