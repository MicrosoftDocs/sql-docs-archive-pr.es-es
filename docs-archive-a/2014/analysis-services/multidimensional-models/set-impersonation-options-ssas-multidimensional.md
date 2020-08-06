---
title: Establecer opciones de suplantación (SSAS-multidimensional) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.impersonationinfo.f1
helpviewer_keywords:
- Impersonation Information dialog box
ms.assetid: 8e127f72-ef23-44ad-81e6-3dd58981770e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b9a8526ff4b8a6dd6f68d13817e427ec70d1953
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675014"
---
# <a name="set-impersonation-options-ssas---multidimensional"></a>Establezca las opciones de suplantación (SSAS - multidimensional)
  Al crear un objeto de `data source` en un modelo de Analysis Services, uno de los valores que debe configurar es una opción de suplantación. Esta opción determina si Analysis Services asume la identidad de una cuenta de usuario de Windows concreta al realizar las operaciones locales relacionadas con la conexión, como cargar un proveedor de datos OLE DB o resolver la información de perfil de usuario en entornos que admiten perfiles de itinerancia.  
  
 Para las conexiones que utilizan la autenticación de Windows, la opción de suplantación también determina la identidad en la que las consultas se ejecuten en el origen de datos externo. Por ejemplo, si establece la opción de suplantación en **contoso\dbuser**, las consultas usadas para recuperar datos durante el procesamiento se ejecutan como **contoso\dbuser** en el servidor de bases de datos.  
  
 Este tema explica cómo establecer las opciones de suplantación en el cuadro de diálogo **Información de suplantación** al configurar un objeto de origen de datos.  
  
## <a name="set-impersonation-options-in-sql-server-data-tools"></a>Establezca las opciones de suplantación en Herramientas de datos de SQL Server  
  
1.  Haga doble clic en un origen de datos en el explorador de soluciones para abrir el Diseñador de origen de datos.  
  
2.  Haga clic en la pestaña **Información de suplantación** en el Diseñador de origen de datos.  
  
3.  Elija una opción descrita en [Opciones de suplantación](#bkmk_options) en este tema.  
  
## <a name="set-impersonation-options-in-management-studio"></a>Establezca las opciones de suplantación en Management Studio  
 En [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], abra el cuadro de diálogo **Información de suplantación** , haga clic en el botón de puntos suspensivos (**…**) para las propiedades siguientes de estos cuadros de diálogo:  
  
-   El cuadro de diálogo**Propiedades de la base de datos** , mediante la propiedad Información de suplantación de origen de datos.  
  
-   El cuadro de diálogo**Propiedades del origen de datos** , mediante la propiedad Información de suplantación.  
  
-   El cuadro de diálogo**Propiedades del ensamblado** , mediante la propiedad Información de suplantación.  
  
##  <a name="impersonation-options"></a><a name="bkmk_options"></a> Opciones de suplantación  
 Todas las opciones están disponibles en el cuadro de diálogo, pero no todas las opciones son adecuadas para cada escenario. Utilice la siguiente información para determinar la mejor opción para el escenario.  
  
 **Utilizar un nombre de usuario y una contraseña específicos**  
 Seleccione esta opción para que el [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objeto use las credenciales de seguridad de una cuenta de usuario de Windows especificada en este formato: *\<Domain name>***\\***\<User account name>* .  
  
 Elija esta opción para usar una identidad de usuario de Windows dedicada con los privilegios mínimos que ha creado específicamente para el acceso a los datos. Por ejemplo, si suele crear una cuenta de uso general para leer los datos que se recuperan en los informes, puede especificar esa cuenta aquí.  
  
 En las bases de datos multidimensionales, se utilizarán las credenciales especificadas para el procesamiento, las consultas ROLAP, los enlaces fuera de línea, los cubos locales, los modelos de minería de datos, las particiones remotas, los objetos vinculados y la sincronización del destino al origen.  
  
 En las bases de datos tabulares, se utilizarán las credenciales especificadas para el procesamiento, las consultas que se ejecutan en un almacén de datos relacional (mediante DirectQuery), los enlaces fuera de línea, las particiones remotas y la sincronización del destino al origen.  
  
 En las instrucciones DMX OPENQUERY, esta opción se omite, y se utilizarán las credenciales del usuario actual en lugar de la cuenta de usuario especificada.  
  
 **Utilizar cuenta de servicio**  
 Seleccione esta opción para que el objeto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] use las credenciales de seguridad asociadas al servicio de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] que administra el objeto. Ésta es la opción predeterminada. En las versiones anteriores, esta era la única opción que podía usar. Podría ser preferible esta opción para supervisar el acceso a los datos en el servicio en lugar de en cuentas de usuario individuales.  
  
 En [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], en función del sistema operativo que use, la cuenta de servicio puede ser NetworkService o una cuenta integrada virtual creada para una instancia específica de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Si elige la cuenta de servicio para una conexión que utiliza la autenticación de Windows, recuerde crear un inicio de sesión de base de datos para esta cuenta y conceder permisos de lectura, ya que se utilizará para recuperar datos durante el procesamiento. Para obtener más información acerca de la cuenta de servicio, vea [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
> [!NOTE]  
>  Al utilizar la autenticación de base de datos, debe elegir la opción de suplantación **Usar la cuenta de servicio** si el servicio se ejecuta bajo la cuenta virtual dedicada para Analysis Services. Esta cuenta tendrá permisos para acceder a los archivos locales. Si el servicio se ejecuta como NetworkService, una alternativa mejor es utilizar una cuenta de usuario de Windows con los privilegios mínimos que tenga los permisos **Permitir el inicio de sesión local** . Según la cuenta que proporcione, también puede que tenga que conceder permisos de acceso al archivo en la carpeta de programas de Analysis Services.  
  
 En las bases de datos multidimensionales, se usarán las credenciales de la cuenta de servicio para el procesamiento, las consultas ROLAP, las particiones remotas, los objetos vinculados y la sincronización del destino al origen.  
  
 En las bases de datos tabulares, se utilizarán las credenciales especificadas para el procesamiento, las consultas que se ejecutan en un almacén de datos relacional (mediante DirectQuery), las particiones remotas y la sincronización del destino al origen.  
  
 Para las instrucciones DMX OPENQUERY, los cubos locales y los modelos de minería de datos, las credenciales del usuario actual se utilizarán aunque elija la opción de cuenta de servicio. La opción de cuenta de servicio no se admite para los enlaces fuera de línea.  
  
> [!NOTE]  
>  Pueden producirse errores al procesar un modelo de minería de datos de un cubo si la cuenta de servicio no tiene permisos de administrador en la instancia de Analysis Services. Para obtener más información, vea [Estructura de minería de datos: problema al procesar cuando el origen de datos es un cubo OLAP](https://go.microsoft.com/fwlink/?LinkId=251610).  
  
 **Utilizar las credenciales del usuario actual**  
 Seleccione esta opción para que el objeto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] use las credenciales de seguridad del usuario actual para los enlaces fuera de línea, las instrucciones DMX OPENQUERY, los cubos locales y los modelos de minería de datos.  
  
 Esta opción no se admite en las bases de datos tabulares.  
  
 Salvo los cubos locales y el procesamiento mediante enlaces fuera de línea, esta opción no se admite para las bases de datos multidimensionales.  
  
 **Predeterminado** o **Heredar**  
 El cuadro de diálogo usa **Predeterminado** para las opciones de suplantación establecidas en el nivel de base de datos y **Heredar** para las opciones de suplantación establecidas en el nivel de origen de datos.  
  
 **Orígenes de datos: opción heredar**  
  
 En el origen de datos, **Heredar** especifica que [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] debe utilizar la opción de suplantación del objeto primario. En un modelo multidimensional, el objeto primario es la base de datos de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Elegir la opción **Heredar** permite administrar de forma centralizada la configuración de suplantación para este y de otros orígenes de datos que forman parte de la misma base de datos. Para que esta opción tenga significado, elija un nombre de usuario de Windows específico y una contraseña en la base de datos. En caso contrario, la combinación de **Heredar** en el origen de datos y **Valor predeterminado** en la base de datos es equivalente a la opción de cuenta de servicio.  
  
 Para especificar un nombre de usuario Windows y una contraseña en la base de datos, haga lo siguiente:  
  
1.  Haga clic con el botón derecho en [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] en la base de datos y seleccione **Propiedades**.  
  
2.  En **Información de suplantación de origen de datos**, especifique el nombre de usuario de Windows y la contraseña.  
  
3.  Haga clic con el botón derecho en cada origen de datos y vea sus propiedades para asegurarse de que cada una usa la opción **Heredar** .  
  
 Para obtener más información sobre la configuración predeterminada en el nivel de base de datos, vea [Establecer propiedades de bases de datos multidimensionales &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md).  
  
 **Bases de datos: opción predeterminada**  
  
 En las bases de datos tabulares, **Predeterminado** significa que se debe utilizar la cuenta de servicio.  
  
 En las bases de datos multidimensionales, **Predeterminado** especifica que se debe utilizar la cuenta de servicio y el usuario actual para las operaciones de minería de datos.  
  
## <a name="see-also"></a>Consulte también  
 [Crear un origen de datos &#40;&#41;de SSAS multidimensional](create-a-data-source-ssas-multidimensional.md)   
 [Establecer propiedades de origen de datos &#40;&#41;de SSAS multidimensional](set-data-source-properties-ssas-multidimensional.md)   
 [Escenarios de implementación de DirectQuery &#40;&#41;tabular de SSAS](../directquery-deployment-scenarios-ssas-tabular.md)  
  
  
