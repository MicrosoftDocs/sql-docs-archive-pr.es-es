---
title: Importar directivas (cuadro de diálogo) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 2601c21ea08d00bf77e9b97a5186f2d6d1200a10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663447"
---
# <a name="import-policies-dialog-box"></a>Importar directivas (cuadro de diálogo)
  Utilice este cuadro de diálogo para importar una o varias directivas (y su condición a la que se hace referencia) que se guardaron como archivos XML, en la instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] actual.  
  
## <a name="options"></a>Opciones  
 **Archivos para importar**  
 Para importar una directiva desde un archivo XML, escriba la ruta de acceso y el nombre del archivo, o use el botón Examinar ( **...** ).  
  
 **Reemplazar duplicados con elementos importados**  
 Seleccione esta opción para sobrescribir cualquier directiva o condición existente del mismo nombre si ya existe en esta instancia de [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Una condición con una directiva dependiente no se puede sobrescribir a menos que la directiva dependiente se esté sobrescribiendo también. Si no se selecciona esta opción, una condición existente que está utilizando la misma expresión de condición no producirá un error.  
  
 **Estado de directiva**  
 Seleccione el estado que desea para la directiva importada:  
  
-   **Conservar el estado de las directivas al importar**  
  
-   **Habilitar todas las directivas al importar**  
  
-   **Deshabilitar todas las directivas al importar**  
  
## <a name="see-also"></a>Consulte también  
 [Administrar servidores mediante administración basada en directivas](administer-servers-by-using-policy-based-management.md)   
 [Importar una directiva de administración basada en directivas](import-a-policy-based-management-policy.md)   
 [Exportar una directiva de administración basada en directivas](export-a-policy-based-management-policy.md)  
  
  
