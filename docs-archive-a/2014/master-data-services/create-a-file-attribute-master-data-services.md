---
title: Crear un atributo de archivo (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating file attributes [Master Data Services]
- attributes [Master Data Services], creating file attributes
ms.assetid: d224886b-2ef1-4658-8b01-2213cc4b8df6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f4f6e2f10a830d089d1d217f7cf54d0b8557add9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669727"
---
# <a name="create-a-file-attribute-master-data-services"></a>Crear un atributo de archivo (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], cree un atributo de archivo para rellenar los valores de atributo con archivos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso para tener acceso al área funcional de **Administración del sistema** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [administradores &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Debe existir una entidad para la que crear el atributo. Para obtener más información, vea [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-file-attribute"></a>Crear un atributo de archivo  
  
1.  En [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], haga clic en **Administración del sistema**.  
  
2.  En la página **Vista de modelo** , en la barra de menús, seleccione **Administrar** y haga clic en **Entidades**.  
  
3.  En la página **Mantenimiento de entidades** , en la lista **Modelo** , seleccione un modelo.  
  
4.  Seleccione la fila para la entidad para la que desea crear un atributo.  
  
5.  Haga clic en **Editar entidad seleccionada**.  
  
6.  En la página **Editar entidad** :  
  
    -   Si el atributo es para miembros hoja, en el panel **Atributos de miembro hoja** , haga clic en **Agregar atributo hoja**.  
  
    -   Si el atributo es para miembros consolidados, en el panel **Atributos de miembro consolidados** , haga clic en **Agregar atributo consolidado**.  
  
    -   Si el atributo es para colecciones, en el panel **Atributos de colección** , haga clic en **Agregar atributo de colección**.  
  
7.  En la página **Agregar atributo** , seleccione la opción **archivo** .  
  
8.  En el cuadro **Nombre** , escriba un nombre para el atributo. Para obtener una lista de palabras que no se deben usar como nombres de atributo, consulte [palabras reservadas &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).  
  
9. En el cuadro **Ancho de píxel de la pantalla** , escriba el ancho de la columna de atributo que se va a mostrar en la cuadrícula del **Explorador** .  
  
10. En la lista **extensión de archivo** , seleccione uno o más tipos de archivo que un usuario puede cargar o deje el valor predeterminado (*. \* ) para permitir todos los tipos de archivo.  
  
11. Si lo desea, seleccione **Habilitar seguimiento de cambios** para realizar el seguimiento de los cambios en los grupos de atributos. Para obtener más información, consulte [Agregar atributos a un grupo de seguimiento de cambios &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
12. Haga clic en **Guardar atributo**.  
  
13. En la página **Mantenimiento de entidades** , haga clic en **Guardar entidad**.  
  
## <a name="see-also"></a>Consulte también  
 [Atributos &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)   
 [Cambiar el nombre de un atributo &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Cree un atributo basado en dominio &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Crear un atributo de texto &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
  
