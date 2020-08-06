---
title: Agregar conocimiento a una base de conocimiento | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: da148a7f-55bc-4990-a157-e61968b831d7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d3450f220b7d879e76c112232081dfec22665dae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663742"
---
# <a name="adding-knowledge-to-a-knowledge-base"></a>Agregar conocimiento a una base de conocimiento
  En este tema se describen las diferentes formas de agregar conocimiento a una base de conocimiento en [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Para poder realizar operaciones de calidad de datos, tiene que tener conocimientos sobre estos. Para adquirirlo, deberá generar y mantener una base de conocimiento de calidad de datos (DQKB), y agregar en ella conocimiento relacionado con un tipo específico de origen de datos. La base de conocimiento es un repositorio de conocimiento sobre los datos que le permite comprenderlos y mantener su integridad.  
  
 La base de conocimiento contiene dominios de datos relacionados con el origen de datos. Para cada dominio de datos, la DQKB almacena todos los términos, errores ortográficos, reglas de validación y de negocios, y datos de referencia identificados que se pueden utilizar para realizar acciones de calidad de datos en el origen de datos. DQS utiliza este conocimiento para identificar los datos incorrectos o no válidos, o para realizar la búsqueda de coincidencias.  
  
 Puede agregar conocimiento a una base de conocimiento de las formas siguientes, bien interactivas o asistidas por PC.  
  
-   [Realizar la detección de conocimiento](#Discovery)  
  
-   [Administrar los valores de datos de un dominio](#ManageDomain)  
  
-   [Importar conocimiento desde un archivo .dqs](#DQSFile)  
  
-   [Importar conocimiento desde un archivo de Excel](#Excel)  
  
-   [Importar de nuevo el conocimiento de un proyecto en la base de conocimiento](#Project)  
  
-   [Utilizar la base de conocimiento de DQS predeterminada](#Default)  
  
##  <a name="perform-knowledge-discovery"></a><a name="Discovery"></a>Realizar la detección de conocimiento  
 La detección de conocimiento analiza una muestra de datos para comprobar si cumplen los criterios de calidad de los datos y, a continuación, agrega el conocimiento adquirido a la base de conocimiento. Este es un proceso asistido por PC que identifica incoherencias y errores de sintaxis en los datos, y que propone cambios en los datos. La actividad de detección de conocimiento es un asistente que incluye una página en la que puede administrar de forma interactiva valores de dominio.  
  
-   Para obtener más información en la documentación, vea [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md).  
  
-   Para obtener un vídeo que muestra cómo realizar la detección de conocimiento, haga clic [aquí](https://msdn.microsoft.com/sqlserver/hh323825.aspx).  
  
##  <a name="manage-data-values-in-a-domain"></a><a name="ManageDomain"></a>Administrar valores de datos en un dominio  
 DQS le permite cambiar y aumentar de forma interactiva los metadatos generados por la actividad de detección de conocimiento asistida por PC. Puede hacerlo en la actividad Administración de dominios, donde puede aplicar un cambio a un valor de datos específico.  
  
-   Para obtener más información en la documentación, vea [Change Domain Values](../../2014/data-quality-services/change-domain-values.md).  
  
-   Para obtener un vídeo que muestra cómo realizar la administración de dominios, haga clic [aquí](https://msdn.microsoft.com/sqlserver/hh323825.aspx). Observe que, en este vídeo, los valores de dominio se cambian en la página Administrar valores del dominio del Asistente para la detección de conocimiento. También puede realizar estos pasos en la página Valores del dominio de la actividad Administración de dominios.  
  
##  <a name="import-knowledge-from-a-dqs-file"></a><a name="DQSFile"></a>Importar conocimiento desde un archivo. DQS  
 Puede importar un dominio desde un archivo de datos .dqs a una base de conocimiento existente, o puede importar una base de conocimiento completa desde un archivo .dqs a una nueva base de conocimiento. Para ello, primero debe exportar un dominio o una base de conocimiento existente a un archivo .dqs. Un archivo .dqs que contiene un dominio incluye todos los datos de este; un archivo .dqs que contiene una base de conocimiento contendrá toda la información de esta, incluidos los dominios y la directiva de coincidencia.  
  
-   Para más información en la documentación, vea [Importar un dominio desde un archivo .dqs](../../2014/data-quality-services/import-a-domain-from-a-dqs-file.md) o [Importar una base de conocimiento desde un archivo .dqs](../../2014/data-quality-services/import-a-knowledge-base-from-a-dqs-file.md).  
  
##  <a name="import-knowledge-from-an-excel-file"></a><a name="Excel"></a>Importar conocimiento desde un archivo de Excel  
 Puede importar valores de dominio desde un archivo de hoja de cálculo de Excel a un dominio o a una base de conocimiento existente. Para ello, primero debe crear una hoja de cálculo de Excel con los valores de dominio que desea importar y asegurarse de que Excel está instalado en el equipo de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] para poder importar valores mediante [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. No se pueden exportar valores de dominio de un dominio o una base de conocimiento a un archivo de Excel.  
  
-   Para más información en la documentación, vea [Importar valores desde un archivo de Excel a un dominio](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md) o [Importar dominios desde un archivo de Excel a la detección del conocimiento](../../2014/data-quality-services/import-domains-from-an-excel-file-in-knowledge-discovery.md).  
  
##  <a name="import-knowledge-from-a-project-back-into-the-knowledge-base"></a><a name="Project"></a>Importar de nuevo el conocimiento de un proyecto en la base de conocimiento  
 Después de ejecutar un proyecto de calidad datos de limpieza o búsqueda de coincidencias utilizando una base de conocimiento, puede importar de nuevo en dicha base de conocimiento el conocimiento creado durante la ejecución del proyecto. Esto le permitirá conservar el conocimiento generado durante el proyecto, así como generar de forma continuada el conocimiento en la base de conocimiento.  
  
-   Para más información en la documentación, vea [Importar valores de un proyecto de limpieza en un dominio](../../2014/data-quality-services/import-cleansing-project-values-into-a-domain.md).  
  
##  <a name="use-the-default-dqs-knowledge-base"></a><a name="Default"></a>Usar la base de conocimiento de DQS predeterminada  
 DQS se suministra con una base de conocimiento denominada Datos de DQS que contiene dominios para datos de direcciones y de empresas de EE. UU. Esta base de conocimiento se puede utilizar para iniciar rápidamente un proyecto sin crear una nueva base de conocimiento. La base de conocimiento Datos de DQS es de solo lectura, pero el administrador de datos puede crear una nueva base de conocimiento basándose en ella.  
  
-   Para obtener más información en la documentación, vea [Using the DQS Default Knowledge Base](../../2014/data-quality-services/using-the-dqs-default-knowledge-base.md).  
  
  
