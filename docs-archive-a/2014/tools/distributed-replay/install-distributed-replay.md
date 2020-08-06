---
title: Instale Distributed Replay desde el símbolo del sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be7c950b886356c08050e37825d5215b62aeb8cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672315"
---
# <a name="install-distributed-replay-from-the-command-prompt"></a>Instalar Distributed Replay desde el símbolo del sistema
  La instalación de una instancia nueva de Distributed Replay en el símbolo del sistema permite especificar las características que se instalarán y cómo se deben configurar. La instalación en el símbolo del sistema admite la instalación, la reparación, la actualización y la desinstalación de los componentes de Distributed Replay. Al realizar la instalación a través del símbolo del sistema, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] admite el modo totalmente silencioso mediante el uso del parámetro /Q.  
  
> [!NOTE]  
>  En instalaciones locales, debe ejecutar el programa de instalación como administrador. Si instala [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] desde un recurso compartido remoto, deberá usar una cuenta de dominio que tenga permisos de lectura y ejecución para dicho recurso.  
  
## <a name="installation-parameters"></a>Parámetros de instalación  
 La lista de las características de nivel superior incluye [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]y Herramientas. La característica Herramientas instalará las herramientas de administración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]y otros componentes compartidos. Para instalar los componentes de Distributed Replay, especifique los siguientes parámetros:  
  
|Componente|Parámetro|  
|---------------|---------------|  
|Controlador de Distributed Replay|**DREPLAY_CTLR**|  
|Servicio cliente de Distributed Replay|**DREPLAY_CLT**|  
|Herramienta de administración|**Herramientas**|  
  
> [!IMPORTANT]  
>  Después de instalar Distributed Replay, debe crear las reglas de firewall en los equipos cliente y de controlador, y conceder a cada equipo cliente permisos en el servidor de destino. Para obtener más información, vea [Completar los pasos posteriores a la instalación](complete-the-post-installation-steps.md).  
  
 Use los parámetros de la tabla siguiente para desarrollar scripts de la línea de comandos para la instalación.  
  
|Parámetro|Descripción|Valores admitidos|  
|---------------|-----------------|----------------------|  
|/CTLRSVCACCOUNT<br /><br /> **Opcional**|Cuenta de servicio para el servicio Distributed Replay Controller.|Comprueba la cuenta y la contraseña|  
|/CTLRSVCPASSWORD<br /><br /> **Opcional**|Contraseña de la cuenta de servicio de Distributed Replay Controller.|Comprueba la cuenta y la contraseña|  
|/CTLRSTARTUPTYPE<br /><br /> **Opcional**|Tipo de inicio para el servicio Distributed Replay Controller.|Automático<br /><br /> Disabled<br /><br /> Manual|  
|/CTLRUSERS<br /><br /> **Opcional**|Especifica los usuarios que tienen permisos para el servicio de Distributed Replay Controller.|Conjunto de cadenas de la cuenta de usuario que usan " " (espacio) para el delimitador<br /><br /> **Importante**: al configurar el servicio Distributed Replay Controller, puede especificar una o más cuentas de usuario que se usarán para ejecutar los servicios Distributed Replay Client. La lista siguiente es una relación de las cuentas admitidas:<br /><br /> Cuenta de usuario de dominio<br /><br /> Cuenta de usuario local creada por el usuario<br /><br /> Administrador<br /><br /> Cuenta virtual y MSA (cuenta de servicio administrada)<br /><br /> Network Services, servicios locales y sistema<br /><br /> <br /><br /> No se aceptan cuentas de grupo (locales o de dominio) y otras cuentas integradas (como Todos).|  
|/CLTSVCACCOUNT<br /><br /> **Opcional**|Cuenta de servicio para el servicio de cliente de Distributed Replay.|Comprueba la cuenta y la contraseña|  
|/CLTSVCPASSWORD<br /><br /> **Opcional**|Contraseña de la cuenta de servicio de Distributed Replay Client.|Comprueba la cuenta y la contraseña|  
|/CLTSTARTUPTYPE<br /><br /> **Opcional**|Tipo de inicio para el servicio de cliente de Distributed Replay.|Automático<br /><br /> Disabled<br /><br /> Manual|  
|/CLTCTLRNAME<br /><br /> **Opcional**|Nombre del equipo con el que se comunica el cliente para el servicio de Distributed Replay Controller.||  
|/CLTWORKINGDIR<br /><br /> **Opcional**|Directorio de trabajo para el servicio de Distributed Replay Client.|Ruta de acceso válida|  
|/CLTRESULTDIR<br /><br /> **Opcional**|Directorio de resultados para el servicio de Distributed Replay Client.|Ruta de acceso válida|  
  
### <a name="sample-syntax"></a>Sintaxis de ejemplo:  
 **Para instalar el componente Distributed Replay Controller**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 **Para instalar el componente Distributed Replay Client**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  
