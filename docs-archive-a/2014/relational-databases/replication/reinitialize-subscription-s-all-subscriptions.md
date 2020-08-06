---
title: 'Reinicialización de suscripciones: todas las suscripciones | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.reinit.all.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: e1122018-9f74-43e3-8489-7eae33ff23d9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 36912663bfc8e3be0fcb899e2a3bbb1f838549bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87750669"
---
# <a name="reinitialize-subscriptions---all-subscriptions"></a>Reinicializar suscripciones: Todas las suscripciones
  El cuadro de diálogo **Reinicializar suscripciones** permite marcar todas las suscripciones a una publicación para reiniciarlas. La reinicialización implica aplicar una instantánea a cada suscriptor; la realiza el Agente de distribución para las suscripciones a publicaciones transaccionales y el Agente de mezcla para las suscripciones a publicaciones de combinación.  
  
## <a name="options"></a>Opciones  
 **Utilizar la instantánea actual**  
 Seleccione esta opción para aplicar la instantánea actual a cada suscriptor la próxima vez que ejecute el Agente de distribución o el Agente de mezcla para la suscripción. Si no hay ninguna instantánea válida disponible, esta opción no puede seleccionarse.  
  
 **Utilizar una instantánea nueva**  
 Seleccione esta opción para reinicializar todas las suscripciones con una instantánea nueva. La instantánea solo puede aplicarse a cada suscriptor tras haber sido generada por el Agente de instantáneas. Si el Agente de instantáneas está configurado para ejecutarse de forma programada, las suscripciones no se reinicializarán hasta la siguiente ejecución programada del mismo.  
  
 Seleccione **Generar la nueva instantánea ahora** para iniciar el Agente de instantáneas de forma inmediata.  
  
 **Cargar los cambios no sincronizados antes de reinicializar**  
 Solo replicación de mezcla. Seleccione esta opción para cargar los cambios pendientes de las bases de datos de suscripciones antes de sobrescribir los datos de los suscriptores con una instantánea.  
  
 Si se agrega, quita o modifica un filtro con parámetros, los cambios pendientes en el suscriptor no se pueden cargar en el publicador durante la reinicialización. Si desea cargar los cambios pendientes, sincronice todas las suscripciones antes de cambiar el filtro.  
  
 **Marcar para reinicializar**  
 Haga clic en esta opción para marcar cada suscripción para reinicializarla. Una vez que hay una instantánea disponible, se aplicará dicha instantánea al suscriptor la próxima vez que se ejecute el Agente de distribución o el Agente de mezcla para la suscripción.  
  
## <a name="see-also"></a>Consulte también  
 [Reinicializar suscripciones](reinitialize-subscriptions.md)  
  
  
