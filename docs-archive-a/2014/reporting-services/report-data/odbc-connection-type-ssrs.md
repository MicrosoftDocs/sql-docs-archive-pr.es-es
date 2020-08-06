---
title: Tipo de conexión ODBC (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 24163866-f37a-4c38-982e-c3d79bf64d4c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2bf5ee6f3eeaa38796e4fa41f3cc0634fd128cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663920"
---
# <a name="odbc-connection-type-ssrs"></a>Tipo de conexión ODBC (SSRS)
  Para incluir los datos de un proveedor de datos ODBC, debe tener un conjunto de datos basado en un origen de datos de informe de tipo ODBC. Este tipo de origen de datos integrado se basa en la extensión de procesamiento de datos ODBC de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Utilice la información de este tema para crear un origen de datos. Para obtener instrucciones paso a paso, vea [Agregar y comprobar una conexión de datos o un origen de datos &#40;generador de informes y SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="connection-string"></a><a name="Connection"></a> Cadena de conexión  
 La cadena de conexión para la extensión de procesamiento de datos de ODBC depende del controlador ODBC que desee. Una cadena de conexión típica contiene pares de nombre/valor que el controlador admite. Por ejemplo, la siguiente cadena de conexión especifica el controlador ODBC para la base de datos de AdventureWorks y Native Client de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
Driver={SQL Server Native Client 10.0};Server=server;Database=AdventureWorks;Trusted_Connection=yes;  
```  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> Credenciales  
 Se necesitan credenciales para ejecutar consultas y obtener una vista previa del informe localmente y desde el servidor de informes.  
  
 Después de publicar el informe, es posible que necesite cambiar las credenciales para el origen de datos de tal forma que, cuando el informe se ejecute en el servidor de informes, los permisos para recuperar los datos sean válidos.  
  
 Si configura el origen de datos ODBC o SQL para que solicite una contraseña o la incluya en la cadena de conexión y un usuario especifica una contraseña con caracteres especiales, como por ejemplo signos de puntuación, algunos controladores de origen de datos subyacentes no podrán validar los caracteres especiales. Cuando procese el informe, es posible que aparezca un mensaje para indicarle que la contraseña no es válida. Si no se puede cambiar la contraseña, hable con el administrador de la base de datos para que las credenciales correctas se almacenen en el servidor de informes como parte de un nombre del origen de datos (DSN) OBDC del sistema. Para obtener información, vea "OdbcConnection.ConnectionString" en la documentación de [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
> [!NOTE]  
>  Se recomienda no agregar información de inicio de sesión, como contraseñas, a la cadena de conexión. El cuadro de diálogo **Origen de datos** del Generador de informes incluye una pestaña independiente para especificar las credenciales.  
  
 Para obtener más información, vea [conexiones de datos, orígenes de datos y cadenas de conexión en Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) o [Especifique las credenciales en generador de informes](../specify-credentials-in-report-builder.md).  
  
  
##  <a name="remarks"></a><a name="Remarks"></a> Comentarios  
 ODBC es una tecnología de acceso a datos anterior que precedió a OLEDB. ODBC solo admite orígenes de datos relacionales. Los proveedores de datos de ODBC se denominan *controladores*. Microsoft y otros proveedores proporcionan los controladores ODBC. Por ejemplo, Microsoft Office instala controladores ODBC que se conectan a los formatos de archivo de Office.  
  
 Para poder crear una cadena de conexión de ODBC, deberá tener instalados los controladores ODBC y crear un equipo o un DSN de sistema. Para recuperar correctamente los datos que desea obtener, deberá proporcionar una sintaxis de consulta que admita el controlador. La compatibilidad con parámetros varía por controlador. Para más información, vea los temas específicos del controlador que seleccione (por ejemplo, [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)).  
  
###### <a name="platform-and-version-information"></a>Información de plataforma y de versión  
 Para más información sobre proveedores de datos ODBC específicos, vea [Orígenes de datos admitidos por Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) en la documentación de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Libros en pantalla](https://go.microsoft.com/fwlink/?linkid=121312) de .  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a> Temas de procedimientos  
 Esta sección contiene instrucciones paso a paso para trabajar con conexiones de datos, orígenes de datos y conjuntos de datos.  
  
 [Agregar y comprobar una conexión de datos o un origen de datos &#40;Generador de informes y SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Crear un conjunto de datos compartido o un conjunto de datos incrustado &#40;Generador de informes y SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Agregar un filtro a un conjunto de datos &#40;Generador de informes y SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a> Secciones relacionadas  
 Estas secciones de la documentación proporcionan información conceptual detallada sobre los datos de informe, así como información de procedimientos acerca de cómo definir, personalizar y usar las partes de un informe que están relacionadas con datos.  
  
 [Agregar datos a un informe &#40;Generador de informes y SSRS&#41;](report-datasets-ssrs.md)  
 Proporciona información general sobre cómo obtener acceso a los datos del informe.  
  
 [Conexiones de datos, orígenes de datos y cadenas de conexión en el Generador de informes](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Proporciona información sobre las conexiones de datos y los orígenes de datos.  
  
 [Conjuntos de datos incrustados y compartidos de informe &#40;Generador de informes y SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Proporciona información sobre conjuntos de datos compartidos e incrustados.  
  
 [Colección Campos del conjunto de datos &#40;Generador de informes y SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Proporciona información sobre la colección de campos de conjunto de datos que genera la consulta.  
  
 [Orígenes de datos admitidos por Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) en la documentación relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Libros en pantalla](https://go.microsoft.com/fwlink/?linkid=121312) de .  
 Proporciona información detallada sobre la compatibilidad de versiones y plataformas para cada extensión de datos.  
  
  
## <a name="see-also"></a>Consulte también  
 [Parámetros de informe &#40;Generador de informes y Diseñador de informes&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrar, agrupar y ordenar datos &#40;Generador de informes y SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Expresiones &#40;Generador de informes y SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
