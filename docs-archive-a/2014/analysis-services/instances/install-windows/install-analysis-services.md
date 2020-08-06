---
title: Instalar Analysis Services en modo tabular | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
author: minewiskan
ms.author: owend
ms.openlocfilehash: a677fd7770f646067cafb8fedf6d3705ccf2de3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744920"
---
# <a name="install-analysis-services-in-tabular-mode"></a>Instalar Analysis Services en mode tabular
  Si está instalando Analysis Services para usar las nuevas características de modelado tabular, debe instalar Analysis Services en un modo de servidor que admita ese tipo de modelo. El modo de servidor es Tabular y se configura durante la instalación.  
  
 Después de instalar el servidor en este modo, puede utilizarlo en soluciones de host que compile en el diseñador de modelos tabular. Se requiere un servidor de modo tabular si desea que los datos de modelo tabulares accedan a través de la red.  
  
 Puede especificar el modo Tabular en el Asistente para la instalación o en una instalación en la línea de comandos. Las siguientes secciones describen cada una de estas opciones.  
  
## <a name="installation-wizard"></a>Asistente para instalación  
 La siguiente lista le muestra qué páginas del Asistente para la instalación de SQL Server se utilizan para instalar Analysis Services en modo Tabular:  
  
1.  Seleccione **Analysis Services** en el árbol de características del programa de instalación.  
  
     ![Árbol de características de instalación que muestra Analysis Services](../../../sql-server/install/media/ssas-setupas.gif "Árbol de características de instalación que muestra Analysis Services")  
  
2.  En la página Configuración de Analysis Services, asegúrese de seleccionar **Modo tabular**.  
  
     ![Página de instalación con opciones de configuración de Analysis Services](../../../sql-server/install/media/ssas-setupasconfig.gif "Página de instalación con opciones de configuración de Analysis Services")  
  
 El modo tabular utiliza el motor analítico en memoria xVelocity (VertiPaq), que es el almacenamiento predeterminado para los modelos tabulares que se implementan en Analysis Services. Después de implementar las soluciones de modelo tabular en el servidor, puede configurar selectivamente las soluciones tabulares para utilizar el almacenamiento en disco de DirectQuery como una alternativa al almacenamiento enlazado a la memoria.  
  
## <a name="command-line-setup"></a>Instalación de línea de Comandos  
 El programa de instalación de SQL Server incluye un nuevo parámetro (`ASSERVERMODE`) que especifica el modo de servidor. En el siguiente ejemplo se muestra una instalación de la línea de comandos que instala Analysis Services en modo de servidor tabular.  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 `INSTANCENAME` debe tener menos de 17 caracteres.  
  
 Todos los valores de cuenta de marcador de posición se deben reemplazar con cuentas y contraseñas válidas.  
  
 Las herramientas como SQL Server Management Studio o [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] no se instalan mediante la sintaxis de la línea de comandos de ejemplo que se proporciona. Para obtener más información acerca de cómo agregar características, consulte [Install SQL Server 2014 desde el símbolo del sistema](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 `ASSERVERMODE` distingue mayúsculas de minúsculas.  Todos los valores se deben expresar en mayúsculas. En la tabla siguiente se describen los valores válidos de `ASSERVERMODE`.  
  
|Value|Descripción|  
|-----------|-----------------|  
|MULTIDIMENSIONAL|Este es el valor predeterminado. Si no establece `ASSERVERMODE`, el servidor se instala en modo de servidor multidimensional.|  
|POWERPIVOT|Este valor es opcional. En ejercicio, si establece el parámetro `ROLE`, el modo de servidor se establece automáticamente en 1, haciendo que `ASSERVERMODE` sea opcional en una instalación de PowerPivot para SharePoint. Para obtener más información, vea [Install PowerPivot from the Command Prompt](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md).|  
|TABULAR|Se requiere este valor si va a instalar Analysis Services en modo tabular utilizando la instalación de la línea de comandos.|  
  
## <a name="see-also"></a>Consulte también  
 [Determinar el modo de servidor de una instancia de Analysis Services](../determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Configurar el acceso in-Memory o DirectQuery para una base de datos de modelo tabular](../../tabular-models/enable-directquery-mode-in-ssms.md)   
 [Modelado tabular &#40;&#41;tabular de SSAS](../../tabular-models/tabular-models-ssas.md)  
  
  
