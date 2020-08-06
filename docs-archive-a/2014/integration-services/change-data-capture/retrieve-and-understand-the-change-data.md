---
title: Recuperar y describir datos modificados | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 62f60bf4a79c39b4f0cb7d1ba8fb3f52680a1f11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747716"
---
# <a name="retrieve-and-understand-the-change-data"></a>Recuperar y describir datos modificados
  En el flujo de datos de un paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que realiza una carga incremental de datos modificados, la primera tarea consiste en ejecutar la consulta que recupera los datos modificados. Esta consulta se ejecuta dentro de un componente de origen en una tarea Flujo de Datos. A continuación, pueden utilizarse transformaciones y destinos de nivel inferior para aplicar los datos modificados a un destino.  
  
> [!NOTE]  
>  La creación de una consulta que contiene una función con valores de tabla es el tercer paso en el proceso de crear un paquete que realiza una carga incremental de datos modificados. Para obtener más información sobre esta consulta, vea [Crear la función para recuperar los datos modificados](create-the-function-to-retrieve-the-change-data.md). Para obtener una descripción del proceso general de creación de un paquete que realiza una carga incremental de los datos modificados, vea [Captura de datos modificados &#40;SSIS&#41;](change-data-capture-ssis.md).  
  
## <a name="adding-the-data-flow-task"></a>Agregar la tarea Flujo de datos  
 En el flujo de datos del paquete, se recuperan los datos modificados, se separan las filas basándose en el tipo de cambio que se produjo y, a continuación, se aplican los cambios al destino.  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a>Para agregar una tarea Flujo de datos al paquete  
  
1.  En la pestaña [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Flujo de control **de** , agregue una tarea Flujo de datos.  
  
2.  Conecte la tarea anterior que preparó la cadena de consulta con la tarea Flujo de datos.  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a>Configurar el componente de origen para consultar los cambios  
 El componente de origen utiliza la cadena de consulta que se preparó y se almacenó en una variable para llamar a la función con valores de tabla que recupera los datos que han cambiado.  
  
> [!NOTE]  
>  Para obtener más información sobre la cadena de consulta que se preparó y se almacenó en una variable, vea [Preparar para consultar datos modificados](prepare-to-query-for-the-change-data.md). Para obtener más información sobre la función con valores de tabla que recupera los datos modificados, vea [Crear la función para recuperar los datos modificados](create-the-function-to-retrieve-the-change-data.md).  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a>Para configurar un origen de OLE DB para recuperar los datos modificados  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en la pestaña **Flujo de datos** , agregue un origen de OLE DB.  
  
2.  En el **Editor de origen de OLE DB**, en la página **Administrador de conexiones** , seleccione las opciones siguientes:  
  
    1.  Configure una conexión válida con una base de datos de origen.  
  
    2.  Para **Modo de acceso a datos**, seleccione **Comando SQL de variable**.  
  
    3.  Para **Nombre de variable**, seleccione **User::SqlDataQuery**.  
  
3.  En el **Editor de origen de OLE DB**, en la página **Columnas** , asegúrese de que todas las columnas que desea están asignadas a columnas de resultados.  
  
## <a name="next-step"></a>siguiente paso  
 Después de haber configurado un origen de OLE DB para recuperar los datos modificados, el paso siguiente consiste en iniciar el diseño del flujo de datos del paquete.  
  
 **Tema siguiente:** [Procesar inserciones, actualizaciones y eliminaciones](process-inserts-updates-and-deletes.md)  
  
  
