---
title: Eliminar objetos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7b20d1eee3e48c5531b6b788e125b943f7606d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661784"
---
# <a name="delete-objects"></a>Eliminar objetos
  Utilice este cuadro de diálogo para eliminar una base de datos de un objeto de base de datos.  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
 **Objeto que se va a eliminar**  
 Muestra los nombres, tipos, propietarios y estado de los objetos que van a eliminarse, así como los mensajes de error generados durante la ejecución.  
  
> [!NOTE]  
>  La ejecución de **Eliminar** en una base de datos equivale a enviar DROP DATABASE en [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Mostrar dependencias**  
 Haga clic para mostrar los objetos que dependen del objeto actualmente seleccionado y de los cuales éste depende (dependencia ascendente y descendente). La información que aparece en el cuadro de diálogo **Mostrar dependencias** es de solo lectura.  
  
> [!NOTE]  
>  El botón **Mostrar dependencias** no aparece para todos los tipos de objetos de base de datos. Para ver las dependencias cuando el botón **Mostrar dependencias** no está disponible, haga clic con el botón derecho en el objeto en el Explorador de objetos y luego haga clic en **Ver dependencias**.  
  
 **Eliminar la información del historial de copia de seguridad y restauración para las bases de datos**  
 Solo aparece cuando se elimina una base de datos; esta casilla hace que el historial de copias de seguridad y restauración de la base de datos se elimine de la base de datos **msdb** .  
  
 **Cerrar conexiones existentes**  
 Solo aparece cuando se elimina una base de datos; esta casilla termina las conexiones a la base de datos.  
  
  
