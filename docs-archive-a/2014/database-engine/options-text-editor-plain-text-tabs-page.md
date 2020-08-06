---
title: Opciones (editor de texto-texto sin formato-página tabulaciones) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
ms.assetid: 07d82d10-bca9-4b37-abbb-58ef9bfb264b
author: rothja
ms.author: jroth
ms.openlocfilehash: 705210c12582723c107283ca00a5cb885ea3ce98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87674992"
---
# <a name="options-text-editor---plain-text---tabs-page"></a>Options (Editor de texto - Texto sin formato - Página Pestañas)
  Utilice este cuadro de diálogo para cambiar el comportamiento del tabulador del Editor de texto que se usa para editar un documento que no esté asociado a ningún lenguaje de desarrollo específico. Para mostrar estas opciones de configuración, haga clic en **Opciones** en el menú **Herramientas** , expanda el **Editor de texto**, expanda **Texto sin formato**y, a continuación, haga clic en **Tabulaciones**.  
  
## <a name="setting-options-in-multiple-locations"></a>Establecer opciones en varias ubicaciones  
 Las opciones del Editor de texto sin formato también se pueden establecer en el cuadro de diálogo **Todos los idiomas General** . Si usa los cuadros de diálogos **Todos los lenguajes** con el fin de establecer diferentes opciones para los demás editores de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , como los editores MDX o DMX, debe restablecer las opciones del Editor de texto sin formato mediante este cuadro de diálogo.  
  
## <a name="indenting"></a>Sangrías  
 **None**  
 No aplica ninguna sangría a la nueva línea que se crea al presionar ENTRAR. El cursor se coloca en la primera columna de la nueva línea.  
  
 **Bloquear**  
 Aplica una sangría a la nueva línea que se crea al presionar ENTRAR a la misma distancia a la que se creó la sangría de la línea anterior.  
  
 **Automática**  
 El editor de texto simple no admite este tipo de formato.  
  
## <a name="tabs"></a>Pestañas  
 **Tamaño de tabulación**  
 Establece la distancia en espacios entre las tabulaciones. El valor predeterminado es cuatro espacios.  
  
 **Tamaño de sangría**  
 Establece el tamaño en espacios de una sangría automática. El valor predeterminado es cuatro espacios. Se insertarán caracteres de tabulación, de espacio o ambos para rellenar el tamaño especificado.  
  
 **Insertar espacios**  
 Inserta únicamente caracteres de espacio, pero no inserta caracteres de tabulación, al aplicar sangrías. Si **Tamaño de sangría** se establece en 5, por ejemplo, se insertan cinco espacios cada vez que se presiona la tecla TAB o el botón **Aumentar sangría** en la barra de herramientas **Formato** .  
  
 **Mantener tabulaciones**  
 Inserta todos los caracteres de tabulación posibles al aplicar sangrías. Cada carácter de tabulación rellena el número de espacios especificados en **Tamaño de tabulación**. Si **Tamaño de sangría** no es un múltiplo par de **Tamaño de tabulación**, se agregarán caracteres de espacio para rellenar la diferencia.  
  
  
