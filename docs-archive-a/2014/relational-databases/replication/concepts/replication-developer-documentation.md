---
title: Guía para desarrolladores&#39;(replicación) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d9651aec1f02d19ea3494abf242f75049a4f33f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748077"
---
# <a name="developer39s-guide-replication"></a>Guía para desarrolladores&#39;(replicación)
  La capacidad de configurar, mantener y supervisar mediante programación una topología de replicación permite simplificar las tareas de replicación repetidas y mejorar la experiencia del usuario en las aplicaciones basadas en la replicación. Al programar la replicación, se puede proporcionar a los usuarios finales funcionalidades de replicación personalizadas sin que sea necesario conocer los procedimientos almacenados de replicación o las aplicaciones ejecutables del agente de replicación, ni tener que usar la interfaz de usuario de replicación que implementa [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 A continuación se muestran escenarios en los que las aplicaciones podrían beneficiarse del acceso mediante programación a servicios de replicación:  
  
-   Al agregar funcionalidades de replicación a una aplicación de usuario final, por ejemplo sincronizar una suscripción de extracción cuando el usuario hace clic en un botón.   
-   Al crear una interfaz de usuario basada en web para administrar la replicación de forma remota.    
-   Al crear una interfaz de usuario personalizada que exponga solo un subconjunto de la funcionalidad de administración, se puede utilizar para administrar varias topologías de replicación de forma remota desde una sola ubicación o que combinen las funcionalidades de administración y sincronización.    
-   Al mejorar una herramienta de supervisión existente agregando la capacidad de supervisar el estado de una publicación, suscripción o en el distribuidor.    
-   Al crear una aplicación personalizada para administrar o sincronizar las suscripciones a un publicador de Oracle.    
-   Al escribir reglas de negocios personalizadas que se ejecutan cuando se sincroniza una suscripción de mezcla.    
-   Al generar scripts de [!INCLUDE[tsql](../../../includes/tsql-md.md)] que se pueden ejecutar varias veces al configurar nuevos suscriptores.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] permite controlar mediante programación los agentes de replicación y administrar y supervisar mediante programación una topología de replicación. Para obtener más información sobre la programación de la replicación, vea [Conceptos de la programación de replicación](replication-programming-concepts.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Conceptos de la programación de replicación](replication-programming-concepts.md)  
 Describe los pasos de planeamiento para desarrollar una aplicación que use la replicación.  
  
 [Conceptos de procedimientos almacenados del sistema de replicación](replication-system-stored-procedures-concepts.md)  
 Describe cómo se pueden usar los procedimientos almacenados del sistema para proporcionar acceso mediante programación en una topología de replicación.  
  
 [Replication Management Objects Concepts (Conceptos de Replication Management Objects)](replication-management-objects-concepts.md)  
 Explica los conceptos para utilizar Replication Management Objects (RMO). El siguiente es un ensamblado de código administrado que encapsula las funcionalidades de replicación para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Conceptos de los ejecutables del Agente de replicación](replication-agent-executables-concepts.md)  
 Describe el uso de los archivos ejecutables del Agente de replicación.  

  
  
