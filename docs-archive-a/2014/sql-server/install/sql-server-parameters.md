---
title: Parámetros de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b885e7616506fd08cae99166cc794dbfb5dac7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87747881"
---
# <a name="sql-server-parameters"></a>Parámetros de SQL Server
  En esta página, establezca los parámetros que utilizará el analizador para el análisis de [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Puede analizar una, varias o todas las bases de datos, analizar archivos de seguimiento que se crearon con [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] y analizar archivos por lotes de SQL.  
  
> [!NOTE]  
>  Se pueden detectar algunos problemas de actualización solo si envía los archivos de seguimiento o los archivos por lotes de SQL que se van a analizar.  
  
## <a name="options"></a>Opciones  
 **Base(s) de datos a analizar**  
 Para analizar todas las bases de datos, active la casilla **todas las bases de datos** . Para analizar una selección de bases de datos, active la casilla situada junto a aquellas bases de datos que desee incluir en el análisis.  
  
 **Analizar archivo(s) de seguimiento**  
 Active esta casilla para analizar los archivos de seguimiento en el sistema de archivos.  
  
 **Ruta de acceso a los archivos de seguimiento**  
 Puede analizar uno o más archivos. Puede ir a una ubicación y seleccionar varios archivos, o puede proporcionar varios nombres de archivo. Utilice la ruta completa de cada archivo, incluya el nombre de éstos y separe las entradas utilizando el carácter de canalización (|).  
  
 Si habilita **analizar archivos de seguimiento**, **siguiente** se deshabilitará hasta que escriba un nombre de ruta de acceso y un nombre de archivo.  
  
 **Analizar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivos por lotes**  
 Active esta casilla para analizar los archivos por lotes de [!INCLUDE[tsql](../../includes/tsql-md.md)] del sistema de archivos.  
  
 **Ruta de acceso a los [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivos por lotes**  
 Puede analizar uno o más archivos por lotes. Puede ir a una ubicación y seleccionar varios archivos, o puede escribir varios nombres de archivo. Utilice la ruta completa de cada archivo, incluya el nombre de éstos y separe las entradas utilizando el carácter de canalización (|).  
  
 Si habilita **analizar archivos por lotes de SQL**, el botón **siguiente** estará deshabilitado hasta que escriba un nombre de ruta de acceso y un nombre de archivo.  
  
 **Separador de lotes de SQL**  
 El texto que se utiliza para separar los lotes de las instrucciones de [!INCLUDE[tsql](../../includes/tsql-md.md)]. El valor predeterminado es **Go**.  
  
## <a name="see-also"></a>Consulte también  
 [Trabajar con el asesor de actualizaciones](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Referencia de la interfaz de usuario del Asesor de actualizaciones](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
