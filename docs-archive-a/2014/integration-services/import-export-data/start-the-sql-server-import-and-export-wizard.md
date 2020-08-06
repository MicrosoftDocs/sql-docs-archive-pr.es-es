---
title: Ejecutar el Asistente para importación y exportación de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 008c541b1f1a295057b0ee7cc384982627b9689a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674911"
---
# <a name="run-the-sql-server-import-and-export-wizard"></a>Ejecutar el Asistente para importación y exportación de SQL Server
  El Asistente para importación y exportación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona el método más sencillo para copiar datos entre orígenes de datos y crear paquetes básicos. Para obtener más información sobre el asistente, vea [SQL Server Asistente para importación y exportación](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)de.  
  
 Para ver un vídeo en el que se muestra cómo usar el Asistente para importación y exportación de SQL Server para crear un paquete que exporta datos de una base de datos de SQL Server a una hoja de cálculo de Microsoft Excel, vea [exportar datos de SQL Server a Excel (SQL Server vídeo)](https://go.microsoft.com/fwlink/?LinkId=131024).  
  
### <a name="to-start-the-sql-server-import-and-export-wizard"></a>Para iniciar el Asistente para importación y exportación de SQL Server  
  
-   En el menú **Inicio** , seleccione **todos los programas**,**Microsoft SQL Server** y, a continuación, haga clic en **importar y exportar datos**.  
  
     O bien  
  
     En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , haga clic con el botón secundario en la carpeta **paquetes SSIS** y, a continuación, haga clic en **Asistente para SSISImport y exportar**.  
  
     O bien  
  
     En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , en el menú **proyecto** , haga clic en **Asistente para SSISImport y exportar**.  
  
     O bien  
  
     En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , conéctese al [!INCLUDE[ssDE](../../includes/ssde-md.md)] tipo de servidor, expanda bases de datos, haga clic con el botón secundario en una base de datos, seleccione **tareas**y, a continuación, haga clic en **importar datos** o **exportar datos**.  
  
     O bien  
  
     En una ventana de símbolo del sistema, ejecute DTSWizard.exe, ubicado en C:\Archivos de programa\Microsoft SQL Server\100\DTS\Binn.  
  
    > [!NOTE]  
    >  En un equipo de 64 bits, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] instala la versión de 64 bits del Asistente para importación y exportación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (DTSWizard.exe). Sin embargo, algunos orígenes de datos, como Access o Excel, solo tienen un proveedor de 32 bits disponible. Para trabajar con estos orígenes de datos, podría tener que instalar y ejecutar la versión de 32 bits del asistente. Para instalar la versión de 32 bits del asistente, seleccione Herramientas cliente o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] durante la instalación.  
  
### <a name="to-import-or-export-data-by-using-the-sql-server-import-and-export-wizard"></a>Para importar o exportar datos con el Asistente para importación y exportación de SQL Server  
  
1.  Inicie el Asistente para importación y exportación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  En las páginas del asistente correspondientes, seleccione un origen y un destino para los datos.  
  
     Los orígenes de datos disponibles incluyen proveedores de datos [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], proveedores OLE DB, proveedores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, proveedores de [!INCLUDE[vstecado](../../includes/vstecado-md.md)], Microsoft Office Excel, Microsoft Office Access y el origen de archivo plano. Dependiendo del origen, se establecen opciones tales como el modo de autenticación, el nombre de servidor, el nombre de base de datos y el formato de archivos.  
  
    > [!NOTE]  
    >  El Proveedor OLE DB de [!INCLUDE[msCoName](../../includes/msconame-md.md)] para Oracle no admite los siguientes tipos de datos de Oracle: BLOB, CLOB, NCLOB, BFILE y UROWID. Por consiguiente, el origen OLE DB no puede extraer datos de tablas que contengan columnas con estos tipos de datos.  
  
     Los destinos de datos disponibles incluyen los proveedores de datos [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], proveedores OLE DB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, Excel, Access y el destino de archivo plano.  
  
3.  Establezca las opciones para el tipo de destino que ha seleccionado.  
  
     Si el destino es una base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], puede especificar lo siguiente:  
  
    -   Indicar si se debe crear una nueva base de datos y establecer las propiedades de base de datos. Las siguientes propiedades no pueden configurarse y el asistente usa los valores predeterminados especificados:  
  
        |Propiedad|Value|  
        |--------------|-----------|  
        |Intercalación|Latin1_General_CS_AS_KS_WS|  
        |modelo de recuperación|Completo|  
        |Usar indización de texto completo|True|  
  
    -   Seleccionar si se deben copiar datos desde tablas o vistas, o copiar los resultados de las consultas.  
  
         Si desea hacer una consulta en los datos de origen y copiar los resultados, puede generar una consulta Transact-SQL. Puede ingresar la consulta Transact-SQL manualmente o usar una consulta guardada en un archivo. El asistente incluye una característica de exploración para buscar el archivo, y el asistente abre automáticamente el archivo y pega su contenido en la página del asistente al seleccionar el archivo.  
  
         Si el origen es un proveedor [!INCLUDE[vstecado](../../includes/vstecado-md.md)], debe usar también la opción para copiar los resultados de las consultas, proporcionando la cadena DBCommand como consulta.  
  
         Si la información de origen es una vista, el Asistente para importación/exportación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convierte automáticamente la vista en una tabla en el destino.  
  
    -   Indicar si la tabla de destino debe quitarse y volver a crearse posteriormente, y si se deben habilitar las inserciones de identidad.  
  
    -   Indicar si se deben eliminar filas o anexar filas en una tabla de destino existente. Si la tabla no existe, el Asistente para importación y exportación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la crea automáticamente.  
  
     Si el destino es un destino de archivo plano, puede especificar lo siguiente:  
  
    -   Especificar el delimitador de fila en el archivo de destino.  
  
    -   Especificar el delimitador de columna en el archivo de destino.  
  
4.  Si se desea, seleccionar una tabla y cambiar las asignaciones entre las columnas de origen y de destino, o cambiar los metadatos de las columnas de destino:  
  
    -   Asignar las columnas de origen a diferentes columnas de destino.  
  
    -   Cambiar el tipo de datos en la columna de destino.  
  
    -   Establecer la longitud de las columnas con tipos de datos de caracteres.  
  
    -   Establecer la precisión y la escala de las columnas con tipos de datos numéricos.  
  
    -   Especifique si la columna puede contener valores NULL.  
  
5.  Si se desea, seleccionar varias tablas y actualizar los metadatos y las opciones para aplicar a esas tablas:  
  
    -   Seleccionar un esquema de destino existente o proporcionar un esquema nuevo al que asignar tablas.  
  
    -   Especificar si se habilitan las inserciones de identidades en las tablas de destino.  
  
    -   Especificar si se quitan y vuelven a crear las tablas de destino.  
  
    -   Especificar si se truncan las tablas de destino existentes.  
  
6.  Guardar y ejecutar un paquete.  
  
     Si se inicia el asistente desde [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o desde el símbolo del sistema, el paquete se puede ejecutar de inmediato. Opcionalmente, puede guardar el paquete en la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de datos **msdb** o en el sistema de archivos. Para obtener más información acerca de la base de datos **msdb** , vea [Administración de paquetes &#40;servicio SSIS&#41;](../service/package-management-ssis-service.md).  
  
     Al guardar el paquete, puede establecer su nivel de protección y, si el nivel utiliza una contraseña, proporcionarla. Para obtener más información acerca de los niveles de protección de paquetes, consulte [Access Control de datos confidenciales en paquetes](../security/access-control-for-sensitive-data-in-packages.md).  
  
     Si se inicia el asistente desde un proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], el paquete no se puede ejecutar desde el asistente. En lugar de ello, el paquete se agrega al proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] desde el cual se inició el asistente. En ese caso, se puede ejecutar el paquete en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
    > [!NOTE]  
    >  En [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] , la opción para guardar el paquete creado por el asistente no está disponible.  
  
## <a name="see-also"></a>Consulte también  
 [Asistente para importación y exportación de SQL Server](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)   
 [Crear paquetes en herramientas de datos de SQL Server](../create-packages-in-sql-server-data-tools.md)  
  
  
