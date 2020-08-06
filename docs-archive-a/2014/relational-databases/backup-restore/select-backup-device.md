---
title: Seleccionar dispositivo de copia de seguridad | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a848f9188eec0ebb09931bca460b0389b9570ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748136"
---
# <a name="select-backup-device"></a>Seleccionar dispositivo de copia de seguridad
  Utilice el cuadro de diálogo **Seleccionar dispositivo lógico de copia de seguridad** para seleccionar un dispositivo de copia de seguridad para la operación de restauración.  
  
 Un dispositivo lógico de copia de seguridad es un dispositivo lógico definido por el usuario que corresponde a un dispositivo físico, ya sea una unidad de cinta o de disco, que proporciona el sistema operativo.  
  
> [!NOTE]  
>  Si una copia de seguridad utiliza varios dispositivos de copia de seguridad, todos deben corresponder a un solo tipo de dispositivo.  
  
 **Para utilizar SQL Server Management Studio a fin de ver el contenido de un dispositivo de copia de seguridad**  
  
-   [Ver el contenido de una cinta o un archivo de copia de seguridad &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Ver las propiedades y el contenido de un dispositivo lógico de copia de seguridad &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Opciones  
 **Dispositivo de copia de seguridad**  
 En el cuadro de lista, seleccione el nombre de un dispositivo lógico de copia de seguridad desde el que desea efectuar la restauración.  
  
 Para obtener información sobre cómo ver el contenido de un dispositivo de copia de seguridad, vea [Ver las propiedades y el contenido de un dispositivo lógico de copia de seguridad &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).  
  
## <a name="remarks"></a>Observaciones  
 Si no ve un dispositivo lógico de copia de seguridad que contenga la copia de seguridad que busca en la lista, puede que dicha copia de seguridad se haya escrito directamente en uno o varios archivos o unidades de cinta. Si es así, cancele el cuadro de diálogo **Seleccionar dispositivo de copia de seguridad** ; en el cuadro de diálogo **Especificar copia de seguridad** , seleccione **Archivo** o **Cinta** en el cuadro de lista **Medio para copia de seguridad** .  
  
## <a name="see-also"></a>Consulte también  
 [Dispositivos de copia de seguridad &#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  
