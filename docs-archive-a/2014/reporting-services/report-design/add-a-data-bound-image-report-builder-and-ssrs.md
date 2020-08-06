---
title: Agregar una imagen enlazada a datos (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea85bdcd6eab04ff51c879a9e790b6e12f73a771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662568"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a>Agregar una imagen enlazada a datos (Generador de informes y SSRS)
  Un informe puede incluir una referencia a una imagen que está almacenada en una base de datos. Este tipo de imagen se conoce como *imagen enlazada a datos*. Las imágenes que aparecen junto a los nombres de producto de una lista de productos son ejemplos de imágenes enlazadas a datos.  
  
 Agregar una imagen enlazada a datos a un encabezado de página o a un pie de página requiere pasos adicionales. Para más información, vea [Encabezados y pies de página &#40;Generador de informes y SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a>Agregar una imagen enlazada a datos  
  
1.  En la vista de diseño del informe, cree una tabla con una conexión a un origen de datos y un conjunto de datos con un campo que contenga los datos binarios de la imagen. Para más información, vea [Tablas &#40;Generador de informes y SSRS&#41;](tables-report-builder-and-ssrs.md).  
  
2.  Inserte una columna en la tabla. Para más información, vea [Insertar o eliminar una columna &#40;Generador de informes y SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  En el menú **Insertar** , haga clic en **Imagen**y, a continuación, haga clic en la fila de datos de la nueva columna.  
  
4.  En la página General del cuadro de diálogo **Propiedades de la imagen** , escriba un nombre en el cuadro de texto **Nombre** o acepte el predeterminado.  
  
5.  (Opcional) En el cuadro de texto **Información sobre herramientas** , escriba el texto que se debe mostrar cuando el usuario mantenga el mouse sobre la imagen en un informe representado para HTML.  
  
6.  En **Seleccionar el origen de la imagen**, seleccione **Base de datos**.  
  
7.  En **Usar este campo**, seleccione el campo que contiene las imágenes en el informe.  
  
8.  En **Usar este tipo MIME**, seleccione el tipo MIME, o el formato de archivo, de la imagen, por ejemplo, bmp.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Aparece un marcador de posición para la imagen en la superficie de diseño del informe.  
  
## <a name="see-also"></a>Consulte también  
 [Imágenes &#40;Generador de informes y SSRS&#41;](images-report-builder-and-ssrs.md)   
 [Incrustar una imagen en un informe &#40;Generador de informes y SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Agregar una imagen externa &#40;Generador de informes y SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)   
 [Cuadro de diálogo de Propiedades de la imagen, General &#40;Generador de informes y SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
