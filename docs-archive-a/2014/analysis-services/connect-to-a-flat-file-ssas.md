---
title: Conectarse a un archivo plano (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connflatfile.f1
ms.assetid: a365991e-eded-4cd8-89c0-0daf6d658d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: e6bee3c8f7f4b255e6985e8d783365bc8a47599e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670019"
---
# <a name="connect-to-a-flat-file-ssas"></a>Conectarse a un archivo plano (SSAS)
  Esta página del **Asistente para la importación de tablas** le permite conectar con un archivo plano (.txt), un archivo separado por caracteres de tabulación (.tab) o un archivo delimitado por comas (.csv). Para tener acceso al asistente desde [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], en el menú **Modelo** , haga clic en **Importar desde el origen de datos**.  
  
 Para conectarse a un archivo plano, debe tener instalado en el equipo el proveedor ACE. Para más información, vea [Orígenes de datos compatibles &#40;SSAS tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
> [!NOTE]  
>  Las credenciales del usuario actual se utilizan al seleccionar un archivo en esta página. Sin embargo, la importación no se realizará correctamente si el usuario especificado en la página Información de suplantación no tiene privilegios suficientes para leer el archivo seleccionado.  
  
## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario  
 **Nombre descriptivo de la conexión**  
 Escriba un nombre único para esta conexión de origen de datos. Este campo es obligatorio.  
  
 **Ruta de acceso del archivo**  
 Especifique la ruta de acceso completa del archivo.  
  
 **Browse**  
 Navegue a una ubicación donde haya un archivo.  
  
 **Separador de columnas**  
 Seleccione los delimitadores de columna disponibles en la lista. Elija un delimitador que no sea probable encontrar en el texto.  
  
|Value|Descripción|  
|-----------|-----------------|  
|Tabulador (t)|Un tabulador (t) separa las columnas.|  
|Coma (,)|Las columnas se separan mediante una coma (,).|  
|Punto y coma (;)|Las columnas se separan mediante un punto y coma (;).|  
|Space ( )|Las columnas se separan mediante un espacio ( ).|  
|Dos puntos (:)|Las columnas se separan mediante dos puntos (:).|  
|Barra vertical (&#124;)|Las columnas se separan mediante una barra vertical (&#124;).|  
  
 **Avanzadas**  
 Especifique las opciones de configuración regional y codificación para el archivo plano.  
  
 **Usar primera fila como encabezados de columna**  
 Especifique si utilizar la primera fila de datos como encabezados de columna de la tabla de destino.  
  
 **Vista previa de datos**  
 Obtenga la vista previa de los datos del archivo seleccionado y use las opciones siguientes para modificar la importación de datos.  
  
> [!NOTE]  
>  Solo las primeras 50 filas del archivo se muestran en esta vista previa.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Casilla en el encabezado de columna**|Active la casilla para incluir la columna en la importación de datos. Desactive la casilla para quitar la columna de la importación de datos.|  
|**Botón de flecha abajo en el encabezado de columna**|Ordene y filtre los datos de la columna.|  
  
 **Borrar filtros de fila**  
 Quite todos los filtros que se aplicaron a los datos en las columnas.  
  
  
