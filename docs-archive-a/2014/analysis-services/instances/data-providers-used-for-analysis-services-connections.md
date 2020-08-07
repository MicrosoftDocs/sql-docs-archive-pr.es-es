---
title: Proveedores de datos usados para conexiones de Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36eacdfc9f4b3469ed28d7dc622c60ceb78ec5f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745497"
---
# <a name="data-providers-used-for-analysis-services-connections"></a>Proveedores de datos usados para las conexiones de Analysis Services
  Analysis Services proporciona tres proveedores de datos para el acceso al servidor y a datos. Todas las aplicaciones que se conectan a Analysis Services lo hacen mediante uno de estos proveedores. Dos de los proveedores, ADOMD.NET y Objetos de administración de Analysis Services (AMO), son proveedores de datos administrados. El proveedor OLE DB de Analysis Services (MSOLAP DLL) es un proveedor de datos nativo.  
  
 En las organizaciones que ejecutan varias versiones de Analysis Services, puede que tenga que instalar versiones más recientes de los proveedores de datos en las estaciones de trabajo de los usuarios que se conectan a datos de Analysis Services. La conexiones a las versiones más recientes de Analysis Services requieren proveedores de datos de la misma versión principal. Por ejemplo, para conectarse a [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], todas las estaciones de trabajo deben tener un proveedor de datos de la versión 2014. Aunque Excel instala los proveedores de datos que necesita para conectarse, ese proveedor puede estar obsoleto con respecto a las instancias de Analysis Services que usa.  
  
 Este tema contiene las secciones siguientes:  
  
 [Cómo determinar la versión del servidor](#bkmk_ServVers)  
  
 [Cómo determinar la versión de los proveedores de datos de Analysis Services](#bkmk_LibUpdate)  
  
 [Dónde obtener versiones más recientes de los proveedores de datos](#bkmk_downloadsite)  
  
 [Proveedor OLE DB de Analysis Services](#bkmk_OLE)  
  
 [ADOMD.NET](#bkmk_ADOMD)  
  
 [AMO](#blkmk_AMO)  
  
##  <a name="how-to-determine-server-version"></a><a name="bkmk_ServVers"></a>Cómo determinar la versión del servidor  
 Conocer la versión de la instancia de Analysis Services le ayudará a determinar si necesita instalar versiones más recientes de los proveedores de datos en las estaciones de trabajo de la organización.  
  
-   En SQL Server Management Studio, conéctese a la instancia de Analysis Services. Haga clic con el botón secundario en la instancia que desea comprobar, seleccione **informes**y haga clic en **General**. La información de la edición y la compilación de versión aparece en el informe.  
  
 El número de compilación principal de la versión inicial de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] es 12.0.2000.9.  
  
 Para más información acerca de cómo obtener información sobre la versión y la compilación, vea [Cómo determinar la versión y la edición de SQL Server y sus componentes](https://support.microsoft.com/kb/321185).  
  
##  <a name="how-to-determine-the-version-of-the-analysis-services-data-providers"></a><a name="bkmk_LibUpdate"></a>Cómo determinar la versión de los proveedores de datos de Analysis Services  
 Los proveedores de datos se instalan con Analysis Services, así como con las aplicaciones cliente que habitualmente se conectan a bases de datos de Analysis Services, como Excel.  
  
 Office 2007 instala proveedores de datos desde SQL Server 2005. Office 2010 instala proveedores de datos desde SQL Server 2008. Office 2013 instala proveedores de datos desde SQL Server 2012. Si está usando varias versiones de Office o SQL Server y la disponibilidad de las características o las conexiones no son lo que esperaba, quizás necesite instalar una versión más reciente de los proveedores de datos. Puede ejecutar varias versiones principales de cada proveedor de datos en paralelo en el mismo equipo.  
  
#### <a name="find-the-file-version-of-the-oledb-provider"></a>Buscar la versión de archivo del proveedor OLEDB  
  
1.  Vaya a \Archivos de programa\Microsoft Analysis Services\AS OLEDB\120.  
  
2.  Haga clic con el botón derecho en msolap120.dll y haga clic en **propiedades**.  
  
 Si no encuentra el archivo en esta ubicación, o si la ruta de acceso de la carpeta incluye AS OLEDB\110 or AS OLEDB\90, está usando una biblioteca antigua y debe instalar una versión más reciente (AS OLEDB\11) para conectarse a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
#### <a name="find-the-file-version-of-adomdnet-and-amo"></a>Buscar la versión de archivo de ADOMD.NET y AMO  
  
1.  Vaya a C:\Windows\Assembly.  
  
2.  Haga clic con el botón derecho en Microsoft.AnalysisServices.AdomdClient y, después, haga clic en **Propiedades**. Haga clic en **Versión**.  
  
     En el caso de AMO, haga clic con el botón secundario en Microsoft.AnalysisServices.  
  
 Para obtener más información acerca de los números de versión y de compilación por versión, vea [Compilaciones de SQL Server en Blogspot](http://sqlserverbuilds.blogspot.com).  
  
##  <a name="where-to-get-newer-version-data-providers"></a><a name="bkmk_downloadsite"></a>Dónde obtener los proveedores de datos de la versión más reciente  
 La versión instalada en el equipo cliente debe coincidir con la versión principal del servidor que proporciona los datos. Si la instalación del servidor es más reciente que los proveedores de datos instalados en las estaciones de trabajo de la red, quizás tenga que instalar bibliotecas más recientes.  
  
#### <a name="find-the-data-providers-on-the-download-site"></a>Buscar los proveedores de datos en el sitio de descarga  
  
1.  Vaya al [Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkID=296473).  
  
2.  Expanda **Instrucciones de instalación**.  
  
3.  Desplácese hacia abajo hasta la sección que contiene los componentes de Analysis Services. ADOMD.NET, el proveedor OLE DB y AMO son el segundo, el tercero y el cuarto elementos de la lista. Todas las bibliotecas están disponibles en versiones de 32 o de 64 bits. Los servidores y las estaciones de trabajo más modernas que ejecuten un sistema operativo de 64 bits necesitarán la versión de 64 bits.  
  
##  <a name="analysis-services-ole-db-provider"></a><a name="bkmk_OLE"></a>Proveedor OLE DB de Analysis Services  
 El proveedor OLE DB de Analysis Services es el proveedor nativo para las conexiones de base de datos de Analysis Services. ADOMD.NET y AMO usan indirectamente MSOLAP, delegando las solicitudes de conexión al proveedor de datos. También puede llamar al proveedor OLE DB directamente desde el código de aplicación, lo que podría hacer si los requisitos de la solución impiden el uso de una API administrada.  
  
 El programa de instalación de SQL Server, Excel y otras aplicaciones que se usan con frecuencia para tener acceso a las bases de datos de Analysis Services instalan automáticamente el proveedor OLE DB para Analysis Services. También puede instalarlo manualmente si lo descarga desde el centro de descarga. De forma predeterminada, el proveedor puede encontrarse en la carpeta \Archivos de programa\Microsoft Analysis Services. El proveedor debe instalarse en cualquier estación de trabajo que se use para tener acceso a datos de Analysis Services.  
  
 MSOLAP130.dll es la versión del proveedor OLE DB para Analysis Services que se incluye en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Otras versiones anteriores recientes incluyen MSOLAP10.dll (para SQL Server 2008 y SQL Server 2008 R2) y MSOLAP90.dll (para SQL Server 2005).  
  
 Los proveedores OLE DB suelen especificarse en las cadenas de conexión. Una cadena de conexión de Analysis Services usa una nomenclatura diferente para hacer referencia al proveedor de OLE DB: MSOLAP. \<version> . dll  
  
 MSOLAP.5.dll es el proveedor OLE DB para Analysis Services que se instala con Excel 2013. Las versiones anteriores, como MSOLAP.4.dll o MSOLAP.3.dll, se encuentran a menudo en estaciones de trabajo que ejecutan versiones anteriores de Excel. Algunas características de Analysis Services, como el complemento PowerPivot, necesitan versiones específicas del proveedor OLE DB. Para más información, vea [Propiedades de cadena de conexión &#40;Analysis Services&#41;](connection-string-properties-analysis-services.md).  
  
##  <a name="adomdnet"></a><a name="bkmk_ADOMD"></a>ADOMD.NET  
 ADOMD.NET es un proveedor de datos administrado que se usa para consultar datos de Analysis Services. Excel emplea ADOMD.NET al conectarse a un cubo concreto de Analysis Services. La cadena de conexión que ve en Excel corresponde a una conexión de ADOMD.NET.  
  
 El programa de instalación de SQL Server instala ADOMD.NET y lo usan las aplicaciones cliente de SQL Server para conectarse a Analysis Services. Office instala esta biblioteca para admitir conexiones de datos de Excel. Como ocurre con otros proveedores de datos incluidos en SQL Server, puede redistribuir ADOMD.NET si usa la biblioteca en código personalizado. También puede descargarlo e instalarlo de forma manual para obtener la versión más reciente (vea [Cómo determinar la versión de los proveedores de datos de Analysis Services](#bkmk_LibUpdate) en este tema).  
  
 Para comprobar la información de la versión de archivos, busque ADOMD.NET en la memoria caché de ensamblados global, donde se muestra como `Microsoft.AnalysisServices.AdomdClient`.  
  
 Al conectarse a una base de datos, las propiedades de cadena de conexión para las tres bibliotecas son iguales en gran medida. Casi todas las cadenas de conexión que defina para ADOMD.NET (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>) funcionarán también para AMO y el proveedor OLE DB de Analysis Services. Para más información, vea [Propiedades de cadena de conexión &#40;Analysis Services&#41;](connection-string-properties-analysis-services.md).  
  
 Para obtener más información sobre la conexión mediante programación, vea [Establishing Connections in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/connections-in-adomd-net).  
  
##  <a name="amo"></a><a name="blkmk_AMO"></a>AMO  
 AMO es un proveedor de datos administrado que se usa para la administración del servidor y la definición de datos. Por ejemplo, SQL Server Management Studio usa AMO para conectarse a Analysis Services.  
  
 El programa de instalación de SQL Server instala AMO y lo usan las aplicaciones cliente de SQL Server para conectarse a Analysis Services. También puede descargarlo e instalarlo de forma manual con AMO en código personalizado (vea [Cómo determinar la versión de los proveedores de datos de Analysis Services](#bkmk_LibUpdate) en este tema). AMO puede encontrarse en la memoria caché global de ensamblados global, como `Microsoft.AnalysisServices`.  
  
 Una conexión que usa AMO suele ser mínima y consta de "Data Source = \<servername> ". Una vez establecida una conexión, use la API para trabajar con las colecciones de base de datos y los objetos principales. Tanto SSDT como SSMS usan AMO para conectarse a una instancia de Analysis Services.  
  
 Para obtener más información sobre la conexión mediante programación, vea [Programming AMO Fundamental Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-fundamental-objects).  
  
## <a name="see-also"></a>Consulte también  
 [Conectar a Analysis Services](connect-to-analysis-services.md)  
  
  
