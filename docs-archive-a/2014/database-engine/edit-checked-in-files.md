---
title: Editar archivos protegidos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e2dbe1aad203dfdc83e438d5b7f4ed19c15038c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87746437"
---
# <a name="edit-checked-in-files"></a>Modificar archivos protegidos
  Normalmente, es necesario desproteger los archivos controlados por código fuente antes de poder modificarlos. Sin embargo, puede configurar [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] para que pueda modificar los archivos que no ha desprotegido. Al hacerlo, los cambios se conservan en la memoria hasta que se guardan los archivos. En ese momento se le pedirá que desproteja el archivo del control de código fuente.  
  
 Si trabaja en un equipo, no es recomendable que permita la modificación de archivos protegidos a menos que el proveedor de control de código fuente permita desproteger la versión local y la versión del servidor. La mayoría de los proveedores no permite desproteger la versión local. Si el proveedor no permite desproteger la versión local y se modifica un archivo protegido, será necesario combinar las versiones en memoria y en el servidor de forma manual antes de poder proteger el archivo. No se permiten las combinaciones automáticas y asistidas por el proveedor en esta situación.  
  
### <a name="to-edit-checked-in-files"></a>Para modificar archivos protegidos  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , expanda la carpeta **Control de código fuente**y, a continuación, haga clic en **Entorno**.  
  
3.  Haga clic en **Permitir que los elementos protegidos se puedan editar**y, a continuación, en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Administrar protecciones](../../2014/database-engine/manage-checkins.md)   
 [Administrar desprotecciones](../../2014/database-engine/manage-checkouts.md)  
  
  
