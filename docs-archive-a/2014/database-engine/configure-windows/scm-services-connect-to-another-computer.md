---
title: Conectarse a otro equipo (Administrador de configuración de SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], other computers
ms.assetid: c4c1e94f-4f5f-431e-8b5b-d5ff97baf723
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f3d478cebc1ca36ccb8f87b0355b7c8fe0a928cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677882"
---
# <a name="connect-to-another-computer-sql-server-configuration-manager"></a>Conectarse a otro equipo (Administrador de configuración de SQL Server)
  En este tema se describe cómo conectar con otro equipo en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Siga el primer procedimiento para abrir [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (mmc) de Administración de equipos de Windows, conéctese al equipo y expanda el árbol Servicios y Aplicaciones. Siga el segundo procedimiento para crear un archivo con un vínculo al Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un equipo remoto.  
  
> [!NOTE]  
>  Algunas acciones no se pueden realizar mediante el Administrador de configuración cuando se conecta de forma remota.  
  
 Para iniciar, detener, pausar o reanudar servicios en otro equipo, también puede conectarse al servidor con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], hacer clic con el botón secundario en el servidor o el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y, a continuación, hacer clic en la acción deseada.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-connect-to-another-computer-with-windows-computer-management"></a>Para conectarse a otro equipo con la Administración de equipos de Windows  
  
1.  En el menú **Inicio** , haga clic con el botón secundario en **mi PC**y, a continuación, haga clic en **administrar.**  
  
2.  En **Administración de equipos**, haga clic con el botón secundario en **Administración del equipo (Local)** y, a continuación, haga clic en **Conectar con otro equipo**.  
  
3.  En el cuadro de diálogo **Seleccionar equipo** , en el cuadro de texto **Otro equipo** , escriba el nombre del equipo que desea administrar y, a continuación, haga clic en **Aceptar**.  
  
     Administración de equipos muestra los servicios que se ejecutan en el equipo remoto. El nodo de nivel superior cambia a **Administración de equipos** \<*remotecomputer*>.  
  
4.  En el árbol de consola, expanda **Servicios y aplicaciones**y, a continuación, expanda **Administrador de configuración de SQL Server** para administrar los servicios del equipo remoto.  
  
#### <a name="to-save-a-link-to-sql-server-configuration-manager-for-another-computer"></a>Para guardar un vínculo al Administrador de configuración de SQL Server para otro equipo  
  
1.  En el menú **Inicio** , haga clic en **Ejecutar**.  
  
2.  En el cuadro **abrir** , escriba `mmc -a` para abrir la [!INCLUDE[msCoName](../../includes/msconame-md.md)] consola de administración de en modo de autor.  
  
3.  En el menú **Archivo** , haga clic en **Agregar o quitar complemento**.  
  
4.  En la ventana **Agregar o quitar complemento** , haga clic en **Agregar**.  
  
5.  En la ventana **Agregar un complemento independiente** , haga clic en **Administración de equipos** y, después, en **Agregar**.  
  
6.  En la ventana **Administración de equipos** , haga clic en **Otro equipo**, escriba el nombre del equipo remoto que desea administrar y, a continuación, haga clic en **Finalizar**.  
  
7.  En la ventana **Agregar un complemento independiente** , haga clic en **Cerrar**.  
  
8.  En la ventana **Agregar o quitar complemento** , haga clic en **Aceptar**.  
  
9. Expanda **Administración de equipos ( ***\<computer name>*** )** y **servicios y aplicaciones**.  
  
10. Haga clic con el botón derecho en **Administrador de configuración de SQL Server**y, después, haga clic en **Nueva ventana desde aquí**.  
  
11. En el menú **Ventana**, haga clic en **Raíz de consola**para regresar a la primera ventana y eliminar la ventana.  
  
12. En el menú **archivo** , haga clic en **Guardar como**y guarde el archivo en la carpeta que desee, con un nombre adecuado con la `.msc` extensión de archivo. Cierre [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.  
  
13. Para abrir el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en el equipo de destino, haga doble clic en el archivo. Si lo desea, guarde un vínculo al archivo en el escritorio o en el menú **Inicio** .  
  
> [!CAUTION]  
>  Cuando utiliza el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en un equipo remoto, el nombre del equipo no es obvio y es posible que se detenga por error o que se configure el equipo equivocado. En la pestaña **Servicio** , marque la casilla **Nombre de host** para confirmar el nombre del equipo antes de modificar un servicio.  
  
## <a name="see-also"></a>Consulte también  
 [Configurar WMI para mostrar el estado del servidor en Herramientas de SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
