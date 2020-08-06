---
title: Usar relaciones de valor en un dominio compuesto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.cdvaluerelations.f1
ms.assetid: 5ee468f0-8538-4620-90e8-63f466c9000e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 135934ec99fed612609e5e1b962f08bb93b98ede
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751485"
---
# <a name="use-value-relations-in-a-composite-domain"></a>Utilizar relaciones de valor en un dominio compuesto
  En este tema se describe cómo ver las combinaciones de valores encontradas para el dominio compuesto durante el proceso de detección de conocimiento de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Esta página muestra el número de repeticiones de las combinaciones de valores. La administración de valores no se admite en los dominios compuestos, por lo que no se puede realizar ninguna operación con estos valores.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Requisitos previos  
 Para ver las relaciones de valor, debe haber creado y abierto un dominio compuesto.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Debe disponer del rol dqs_kb_editor o dqs_administrator en la base de datos DQS_MAIN para ver las relaciones de valor de un dominio compuesto.  
  
##  <a name="view-value-relations"></a><a name="Use"></a>Ver relaciones de valor  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Ejecute la aplicación Data Quality Client](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  En la página de inicio de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , abra o cree una base de conocimiento. Seleccione **Administración de dominios** como actividad y, a continuación, haga clic en **Abrir** o en **Crear**. Para obtener más información, consulte [Crear una base de conocimiento](../../2014/data-quality-services/create-a-knowledge-base.md) o [Abrir una base de conocimiento](../../2014/data-quality-services/open-a-knowledge-base.md).  
  
3.  En la **Lista de dominios** de la página **Administración de dominios** , seleccione el dominio compuesto para el que desea crear una regla de dominio, o cree un nuevo dominio compuesto. Si necesita crear un nuevo dominio, vea [Create a Composite Domain](../../2014/data-quality-services/create-a-composite-domain.md).  
  
4.  Haga clic en la pestaña **Relaciones de valor** .  
  
5.  Vea las frecuencias mostradas para cada combinación de valores.  
  
    > [!NOTE]  
    >  La tabla **Valor** muestra las combinaciones de valores existentes en el dominio compuesto. Cada uno de los valores se muestra en el dominio individual al que se aplica. La ordenación predeterminada de la tabla de relaciones es por frecuencia, pero puede hacer clic en otra columna para ordenar por dicha columna. Solo se muestran aquellos valores con una frecuencia mayor o igual que 20.  
  
6.  No se puede cambiar ninguno de los valores de la tabla. Si ha realizado otras operaciones, haga clic en **Finalizar** para completar la actividad de administración de dominios. En caso contrario, haga clic en **Cancelar**.  
  
##  <a name="follow-up-after-viewing-value-relations"></a><a name="FollowUp"></a>Seguimiento: después de ver las relaciones de valor  
 Una vez vistas las relaciones de valor, puede realizar otras tareas de administración en el dominio, ejecutar la detección de conocimiento para agregar conocimiento al dominio o agregar a este una directiva de coincidencia. Para más información, vea [Realizar la detección de conocimiento](../../2014/data-quality-services/perform-knowledge-discovery.md), [Administrar un dominio](../../2014/data-quality-services/managing-a-domain.md) o [Crear una directiva de coincidencia](../../2014/data-quality-services/create-a-matching-policy.md).  
  
  
