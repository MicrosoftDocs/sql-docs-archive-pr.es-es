---
title: Configuración del regulador de recursos utilizando una plantilla | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62edb23cf55a953cb0fef54f002f8eaaa16f58ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87676461"
---
# <a name="configure-resource-governor-using-a-template"></a>Configurar el regulador de recursos utilizando una plantilla
  Puede configurar el regulador de recursos utilizando una plantilla que se proporciona en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Antes de empezar:**  [Permisos](#Permissions)  
  
-   **Para crear un grupo de cargas de trabajo mediante:** [una plantilla](#ConfRGTemplate)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
 Siga los pasos que se detallan a continuación para abrir y modificar una plantilla que crea un grupo de recursos de servidor y un grupo de cargas de trabajo para el grupo de recursos. Además, esta plantilla le permite crear una función clasificadora definida por el usuario que enruta las nuevas conexiones al grupo predeterminado o al grupo de cargas de trabajo que está creando.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] del regulador de recursos de la plantilla requieren el permiso CONTROL SERVER.  
  
##  <a name="configure-resource-governor-using-a-template"></a><a name="ConfRGTemplate"></a> Configurar el regulador de recursos utilizando una plantilla  
 **Para configurar el regulador de recursos utilizando una plantilla en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], en el menú **Ver** , haga clic en el **Explorador de plantillas**.  
  
2.  En **Explorador de plantillas**, expanda **Regulador de recursos**y, luego, haga doble clic en **Configurar regulador de recursos**.  
  
3.  En **Conectar al motor de base de datos**, escriba la información necesaria y, a continuación, haga clic en **Aceptar**. La plantilla Configure Resource Governor.sql se proporciona junto con el Editor de consultas. Utilice esta plantilla para crear y configurar un grupo de recursos de servidor, un grupo de cargas de trabajo y una función clasificadora.  
  
4.  Para modificar los valores de la plantilla, pulse CTRL+MAYÚS+M. En el cuadro de diálogo **Especificar valores para parámetros de plantilla** , escriba los valores que desea utilizar.  
  
5.  Para guardar los cambios que realice en la plantilla, haga clic en **Aceptar**.  
  
6.  Para ejecutar la consulta, haga clic en **Ejecutar**.  
  
## <a name="see-also"></a>Consulte también  
 [Regulador de recursos](resource-governor.md)   
 [Habilitar el regulador de recursos](enable-resource-governor.md)   
 [Grupo de recursos de servidor del regulador de recursos](resource-governor-resource-pool.md)   
 [Grupos de cargas de trabajo del regulador de recursos](resource-governor-workload-group.md)   
 [Función clasificadora del regulador de recursos](resource-governor-classifier-function.md)   
 [Ver las propiedades del regulador de recursos](view-resource-governor-properties.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
