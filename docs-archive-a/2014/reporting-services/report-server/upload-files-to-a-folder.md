---
title: Cargar archivos a una carpeta | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfb595ed6059436d17cb82262f5d1975a8397dbd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672610"
---
# <a name="upload-files-to-a-folder"></a>Cargar archivos a una carpeta
  Puede cargar archivos desde el sistema de archivos y almacenarlos en una base de datos del servidor de informes como elementos administrados. Lo que sucede al cargar el archivo depende del tipo de archivo.

-   Cargar un archivo .rdl equivale a publicar un informe.

-   Al cargar cualquier otro tipo de archivo, éste se agrega a la base de datos del servidor de informes como un objeto binario único. Estos archivos se publican en un servidor de informes como recurso. Los recursos pueden ser cualquier tipo de archivo. Si la extensión de archivo corresponde a la de un tipo MIME conocido, se utilizará un icono de dicho tipo MIME para identificar el tipo de recurso. De lo contrario, los recursos se indican mediante un icono de archivo genérico.

> [!NOTE]
>  No se pueden cargar archivos de origen de datos de informes (.rds) para crear un origen de datos compartido. Los archivos .rds solo se utilizan en el Diseñador de informes. No puede proporcionar el contenido para un elemento de origen de datos compartido que se defina y administre mediante el Administrador de informes. Como alternativa a la carga, se puede escribir un script que cree un origen de datos compartido basado en un archivo .rds.

 [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]determina el tamaño de archivo máximo para los elementos cargados. De manera predeterminada, el tamaño máximo es de 4 megabytes (MB).

 Visualmente, los archivos que se cargan a la base de datos del servidor de informes aparecen representados en la jerarquía de carpetas con los siguientes iconos.

 Icono de informe ![icono](../media/hlp-16doc.gif "Icono de informe") de informe

 Icono de ![modelo](../media/model-icon.gif "Icono de modelo") icono de modelo de informe

 icono de ![recurso genérico](../media/hlp-16file.gif "Icono de recurso genérico") icono de recurso genérico

 Al cargar un archivo, éste se sitúa siempre en la carpeta seleccionada. Puede navegar en primer lugar hasta la carpeta en la que desea hospedar el elemento o bien puede cargar el archivo y moverlo después a la ubicación final.

 Para cargar un archivo, use el Administrador de informes. Podrá cargar archivos a un servidor de informes dependiendo de qué tareas formen parte de su asignación de roles. Si utiliza la seguridad predeterminada, solo los administradores locales podrán agregar elementos a un servidor de informes. Si está habilitado el rol Mis informes, cada usuario que disponga de una carpeta Mis informes tendrá permiso para cargar archivos a esa carpeta. Si utiliza asignaciones de roles personalizados, deberán incluir las tareas compatibles con la administración de carpetas.

|Para hacer esto|Incluya estas tareas|
|----------------|-------------------------|
|Cargar un archivo .rdl a una carpeta|Administrar informes|
|Cargar cualquier archivo como objeto binario|Administrar recursos|
|Ver el contenido de una carpeta|Ver recursos, Ver informes|

## <a name="see-also"></a>Consulte también
 [Administrador de informes &#40;modo nativo de SSRS&#41;].. /report-manager-ssrs-native-mode.md) [conceder permisos en un servidor de informes en modo nativo](../security/granting-permissions-on-a-native-mode-report-server.md) [tareas y permisos](../security/tasks-and-permissions.md) [cargar un archivo o informe &#40;administrador de informes&#41;](../reports/upload-a-file-or-report-report-manager.md)


