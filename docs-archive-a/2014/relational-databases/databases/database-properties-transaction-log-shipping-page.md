---
title: Propiedades de la base de datos (página Trasvase de registros) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd36b3bc56bcd48c53871c9bc1e334d72c80ac78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87751125"
---
# <a name="database-properties-transaction-log-shipping-page"></a>Propiedades de la base de datos (página Trasvase de registros)
  Utilice esta página para configurar y modificar las propiedades de trasvase de registros de una base de datos.  
  
 Para obtener una explicación de los conceptos relacionados con el trasvase de registros, vea [Acerca del trasvase de registros &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
## <a name="options"></a>Opciones  
 **Habilitar ésta como base de datos principal en una configuración de trasvase de registros**  
 Habilita esta base de datos como base de datos principal de trasvase de registros. Active esta opción y configure las opciones restantes de esta página. Si desactiva esta casilla, la configuración de trasvase de registros se quitará de esta base de datos.  
  
 **Configuración de copia de seguridad**  
 Haga clic en **Configuración de copia de seguridad** para configurar parámetros de programación, ubicación, alerta y archivado de la copia de seguridad.  
  
 **Programación de copia de seguridad**  
 Muestra la programación de copia de seguridad seleccionada para la base de datos principal. Haga clic en **Configuración de copia de seguridad** para modificar estos parámetros.  
  
 **Última copia de seguridad creada**  
 Indica la fecha y hora de la última copia de seguridad del registro de transacciones de la base de datos principal.  
  
 **Instancias de servidores secundarios y bases de datos**  
 Presenta una lista con los servidores secundarios y bases de datos configurados para esta base de datos principal. Resalte una base de datos y haga clic en **...** para modificar los parámetros asociados a esta base de datos secundaria.  
  
 **Add (Agregar)**  
 Haga clic en **Agregar** para agregar una base de datos secundaria a la configuración de trasvase de registros de esta base de datos principal.  
  
 **Remove**  
 Quita una base de datos seleccionada de esta configuración de trasvase de registros. Seleccione la base de datos y, a continuación, haga clic en **Quitar**.  
  
 **Utilizar una instancia del servidor de supervisión**  
 Establece una instancia del servidor de supervisión para esta configuración de trasvase de registros. Active la casilla **Utilizar una instancia del servidor de supervisión** y, a continuación, haga clic en **Configuración** para especificar la instancia.  
  
 **Instancia del servidor de supervisión**  
 Indica la instancia del servidor de supervisión actual para esta configuración de trasvase de registros.  
  
 **Configuración**  
 Configura la instancia del servidor de supervisión para una configuración de trasvase de registros. Haga clic en **Configuración** para configurar esta instancia.  
  
 **Incluir configuración**  
 Genera un script para configurar el trasvase de registros con los parámetros seleccionados. Haga clic en **Incluir configuración**y, a continuación, elija un destino de salida para el script.  
  
> [!IMPORTANT]  
>  Antes de crear scripts para la configuración de una base de datos secundaria, debe invocarse el cuadro de diálogo **Configuración de base de datos secundaria** . Al invocar este cuadro de diálogo, se establece una conexión al servidor secundario y se recupera la configuración actual de la base de datos secundaria, que es necesaria para generar el script.  
  
## <a name="see-also"></a>Consulte también  
 [Procedimientos almacenados del trasvase de registros &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql)   
 [Tablas de trasvase de registros &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-tables-transact-sql)  
  
  
