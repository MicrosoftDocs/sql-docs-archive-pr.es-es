---
title: 'Lección 6: ejecutar la aplicación de esquema RDL (VB-C #) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2cd2386-2df8-4b69-ab81-9ad1a31f6d27
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5a0fc2cd9c12b4b1602f517dc215ca44e686c663
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743703"
---
# <a name="lesson-6-run-the-rdl-schema-application-vb-c"></a>Lección 6: ejecutar la aplicación de esquema RDL (VB-C #)
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ofrece dos métodos para generar y ejecutar una aplicación de consola desde el entorno de desarrollo integrado (IDE):  
  
-   Iniciar (con depuración)  
  
-   Iniciar sin depuración  
  
### <a name="to-build-and-run-the-samplerdlschema-application"></a>Para generar y ejecutar la aplicación SampleRDLSchema  
  
1.  En el menú **Depurar**, haga clic en **Iniciar sin depurar**. Esto garantiza que la ventana de la consola seguirá abierta cuando el programa se haya acabado de ejecutar.  
  
     La aplicación escribe lo siguiente en la consola:  
  
    ```  
    Loading Report Definition  
    Updating Report Definition  
    - Old Description: <Old Report Description>  
    - New Description: <New Report Description>  
    Publishing Report Definition  
    ```  
  
2.  Presione cualquier tecla para cerrar la consola.  
  
    > [!NOTE]  
    >  Los errores que se produzcan se escribirán en la consola.  
  
3.  Cuando la aplicación de ejemplo finaliza la ejecución de una copia actualizada del informe, la guarda en el servidor de informes.  
  
## <a name="see-also"></a>Consulte también  
 [Actualizar informes con clases generadas a partir del esquema RDL &#40;tutorial de SSRS&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Lenguaje RDL (Report Definition Language) &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
