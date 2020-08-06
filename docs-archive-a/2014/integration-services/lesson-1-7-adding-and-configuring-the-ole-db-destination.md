---
title: 'Paso 7: Agregar y configurar el destino de OLE DB | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 442c841d-d528-4bf0-8724-7156f909ee50
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da917ccc4ca756c2442e70477976b5a71f7eb56e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87673120"
---
# <a name="step-7-adding-and-configuring-the-ole-db-destination"></a>Paso 7: Adición y configuración del destino de OLE DB
  Ahora, el paquete puede extraer datos de un origen de archivo plano y transformar dichos datos en un formato compatible con el destino. La tarea siguiente consiste realmente en cargar los datos transformados en el destino. Para cargar los datos, debe agregar un destino de OLE DB al flujo de datos. El destino de OLE DB puede utilizar una tabla de bases de datos, una vista o un comando SQL para cargar datos en distintas bases de datos compatibles con OLE DB.  
  
 En este procedimiento, se agrega y configura un destino de OLE DB para utilizar el administrador de conexiones de OLE DB creado con anterioridad.  
  
### <a name="to-add-and-configure-the-sample-ole-db-destination"></a>Para agregar y configurar un destino de OLE DB de ejemplo  
  
1.  En el **cuadro de herramientas de SSIS**, expanda **otros destinos**y arrastre **OLE DB destino** a la superficie de diseño de la pestaña **flujo de datos** . Coloque el OLE DB destino directamente debajo de la transformación **lookup Date Key** .  
  
2.  Haga clic en la transformación **Lookup Date Key** y arrastre la flecha verde hasta el **Destino de OLE DB** que acaba de agregar para conectar los dos componentes entre sí.  
  
3.  En el cuadro de diálogo **Selección de entrada y salida** , en el cuadro de lista **Salida** , haga clic en **Salida de entradas coincidentes de búsqueda**y, después, haga clic en **Aceptar**.  
  
4.  En la superficie de diseño **Flujo de datos** , haga clic en **Destino de OLE DB** en el componente **Destino de OLE DB** que acaba de agregar y cambie el nombre por **Sample OLE DB Destination**.  
  
5.  Haga doble clic en **Sample OLE DB Destination**.  
  
6.  En el cuadro de diálogo **Editor de destino de OLE DB** , asegúrese de que **localhost.AdventureWorksDW2012** está seleccionado en el cuadro **Administrador de conexiones OLE DB** .  
  
7.  En el cuadro **Nombre de la tabla o la vista** , escriba o seleccione **[dbo].[FactCurrencyRate]**.  
  
8.  Haga clic en el botón **Nuevo** para crear una nueva tabla.  Cambie el nombre de la tabla en el script a **NewFactCurrencyRate**.  Haga clic en **OK**.  
  
9. Al hacer clic en **Aceptar**, se cerrará el cuadro de diálogo y el **Nombre de la tabla o la vista** cambiará automáticamente a **NewFactCurrencyRate**.  
  
10. Haga clic en **Asignaciones**.  
  
11. Compruebe que las columnas de entrada **AverageRate**, **CurrencyKey**, **EndOfDayRate**y **DateKey** están correctamente asignadas a las columnas de destino. Si hay columnas con el mismo nombre asignadas, la asignación es correcta.  
  
12. Haga clic en **OK**.  
  
13. Haga clic con el botón derecho en **Sample OLE DB Destination** y haga clic en **Propiedades**.  
  
14. En el ventana Propiedades, compruebe que la `LocaleID` propiedad está establecida en **inglés (Estados Unidos)** y que la `DefaultCodePage` propiedad está establecida en **1252**.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
 [Paso 8: Facilitar la comprensión del paquete de la lección 1](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
## <a name="see-also"></a>Consulte también  
 [Destino de OLE DB](data-flow/ole-db-destination.md)  
  
  
