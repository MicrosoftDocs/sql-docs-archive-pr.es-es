---
title: 'Lección 2: Especificar información de conexión (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745671"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Lección 2: Especificar información de conexión (Reporting Services)
  Después de agregar un informe al proyecto Tutorial, necesita definir un *origen de datos*, que es la información de conexión que el informe usa para tener acceso a los datos procedentes de una base de datos relacional, una base de datos multidimensional u otro recurso.  
  
 En esta lección usará la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] como origen de datos. En este tutorial se da por supuesto que esta base de datos se encuentra en una instancia predeterminada de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] que está instalada en el equipo local.  
  
### <a name="to-set-up-a-connection"></a>Para configurar una conexión  
  
1.  En el panel **datos de informe** , haga clic en **nuevo** y, a continuación, haga clic en **origen de datos.**  
  
    > [!NOTE]  
    >  Si el panel **Datos de informe** no está visible, haga clic en **Datos de informe** en el menú **Ver**.  
  
2.  En **Nombre**, escriba [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].  
  
3.  Asegúrese de que está seleccionado **Conexión incrustada** .  
  
4.  En **Tipo**, seleccione **Microsoft SQL Server**.  
  
5.  En **Cadena de conexión**, escriba lo siguiente:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     Esta cadena de conexión da por supuesto que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], el servidor de informes y la base de datos [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] están instalados en el equipo local, y que el usuario tiene permiso para iniciar una sesión en la base de datos [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] .  
  
    > [!NOTE]  
    >  Si utiliza [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] con Advanced Services o una instancia con nombre, la cadena de conexión debe incluir información de la instancia:  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  Para obtener más información sobre las cadenas de conexión, vea [conexiones de datos, orígenes de datos y cadenas de conexión en Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) y [propiedades del origen de datos (cuadro de diálogo), general](data-source-properties-dialog-box-general.md).  
  
6.  Haga clic en **Credenciales** en el panel izquierdo y haga clic en **Usar autenticación de Windows (seguridad integrada)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]origen [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] de datos se agrega al panel **datos de informe** .  
  
## <a name="next-task"></a>Tarea siguiente  
 Ha definido correctamente una conexión a la base de datos de ejemplo [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . A continuación, creará el informe. Vea [Lección 3: Definir un conjunto de datos para el informe de tabla &#40;Reporting Services&#41;;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Consulte también  
 [Data Connections, Data Sources, and Connection Strings in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
