---
title: Evaluar una directiva de administración basada en directivas desde un objeto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: b9e9d646-4894-4dee-a02a-0c71a8dc020e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f0de02092c87a727b723a5940805f34a75052e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674768"
---
# <a name="evaluate-a-policy-based-management-policy-from-an-object"></a>Evaluar una directiva de administración basada en directivas desde un objeto
  En este tema se describe cómo evaluar una directiva de una instancia de servidor, una base de datos o un objeto de base de datos en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para evaluar una directiva de un objeto mediante:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitaciones y restricciones  
  
-   El modo de ejecución se define como parte de la directiva y no se puede cambiar en el cuadro de diálogo **Evaluar directivas** .  
  
-   El cuadro de diálogo **Evaluar directivas** solo muestra las directivas apropiadas para el objeto de base de datos.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Requiere la pertenencia al rol PolicyAdministratorRole en la base de datos msdb.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy-from-an-object"></a>Para evaluar una directiva de un objeto  
  
1.  En el Explorador de objetos, haga clic con el botón derecho en una instancia de servidor, base de datos u objeto de base de datos, elija **Directivas**y, después, seleccione **Evaluar**.  
  
2.  En el cuadro de diálogo **Evaluar directivas** , seleccione una o varias directivas y haga clic en **Evaluar** para ejecutar la directiva en modo de evaluación. De esta forma se genera un informe de compatibilidad para el conjunto de destino, pero no se vuelve a configurar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ni se exige la compatibilidad en el futuro. En los destinos que no obedecen las directivas seleccionadas y que tienen propiedades que pueden estar reconfiguradas por la administración basada en directivas, puede exigir la compatibilidad de la directiva haciendo clic en **Aplicar**. Para obtener más información acerca de las opciones disponibles en el cuadro de diálogo **Evaluar directivas** , vea [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md), [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md)y [Results Detailed View Dialog Box](results-detailed-view-dialog-box.md).  
  
3.  Cuando termine, haga clic en **Cerrar**.  
  
  
