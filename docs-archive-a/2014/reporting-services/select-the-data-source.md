---
title: Seleccionar el origen de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 641aa04f7fe658123aa21cc1bd21264ec0ee28ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744995"
---
# <a name="select-the-data-source"></a>Seleccionar el origen de datos
  Utilice esta página del Asistente para informes para definir un origen de datos para el informe.  
  
## <a name="options"></a>Opciones  
 **Origen de datos compartido**  
 Seleccione **Origen de datos compartido** para usar un origen de datos compartido predefinido que tiene ya la información de conexión del origen de datos que quiere usar. La lista contiene todos los orígenes de datos compartidos que se incluyen en el proyecto.  
  
 **Nuevo origen de datos**  
 Seleccione **Nuevo origen de datos** para definir un nuevo origen de datos. La información del origen de datos se utilizará solamente con el informe actual.  
  
 **Nombre**  
 Escriba un nombre para la conexión con el origen de datos. Dicho nombre debe ser único en el informe.  
  
 **Tipo**  
 Seleccione el tipo de origen de datos que está usando (por ejemplo, si está usando una [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de datos, elija [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).  
  
 **Cadena de conexión**  
 Escriba una cadena de conexión para el origen de datos. Para obtener más información sobre las cadenas de conexión, vea [conexiones de datos, orígenes de datos y cadenas de conexión en Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
 Haga clic en **Editar** para especificar el servidor del origen de datos en el cuadro de diálogo **Propiedades de conexión** . Puede especificar un origen de datos local o remoto.  
  
 Haga clic en **Credenciales** para suministrar las credenciales de la base de datos. Como mínimo, las credenciales que especifique deben ser suficientes para poder conectarse al origen de datos con fines de diseño de informes. Cuando el informe se implemente en un servidor de informes, las credenciales de la base de datos deben adaptarse a todos los usuarios del informe. Por ejemplo, si quiere que todos los usuarios del informe se conecten al origen de datos usando sus credenciales, elija **Usar autenticación de Windows (seguridad integrada)**. Las credenciales que especifique deben ser válidas para el origen de datos; por tanto, si elige la autenticación de Windows, asegúrese de que el origen de datos acepta las conexiones de todas las cuentas de usuario que ejecutarán el informe. Las credenciales de la base de datos pueden administrarse independientemente del informe. Para obtener más información, vea [Administrar orígenes de datos de informe](report-data/manage-report-data-sources.md).  
  
 **Convertir en origen de datos compartido**  
 Seleccione esta opción para almacenar el origen de datos en el proyecto como origen de datos compartido, en lugar de en el informe. De ese modo, puede utilizarlo como origen de datos para otros informes en el proyecto.  
  
## <a name="see-also"></a>Consulte también  
 [Conexiones de datos u orígenes de datos incrustados y compartidos &#40;Generador de informes y SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Especificar información de credenciales y conexión para los orígenes de datos de informes](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Reporting Services servidor de informes](../../2014/reporting-services/reporting-services-report-server.md)   
 [Archivo de configuración RSReportDesigner](report-server/rsreportdesigner-configuration-file.md)   
 [Conexiones de datos, orígenes de datos y cadenas de conexión en Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Ayuda del Asistente para informes](../../2014/reporting-services/report-wizard-help.md)  
  
  
