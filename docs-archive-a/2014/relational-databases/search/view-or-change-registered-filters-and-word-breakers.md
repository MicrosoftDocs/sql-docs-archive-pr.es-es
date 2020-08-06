---
title: Ver o cambiar los filtros y separadores de palabras registrados | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], word breakers
- full-text search [SQL Server], filters
- filters [full-text search]
- word breakers [full-text search]
ms.assetid: f88c54df-b1aa-4701-807f-dc92c32363fd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79ad7f1f7df15fed21a132bbe253adc7185d8c06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745165"
---
# <a name="view-or-change-registered-filters-and-word-breakers"></a>Ver o cambiar los filtros y separadores de palabras registrados
  Después de instalar o desinstalar filtros o separadores de palabras en un sistema, los cambios no se aplican automáticamente en las instancias de servidor. En este tema se describe cómo ver los filtros o separadores de palabras actualmente registrados y cómo registrar filtros y separadores de palabras recién instalados en una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="to-view-a-list-of-languages-whose-word-breakers-are-currently-registered"></a>Para ver una lista de idiomas con separadores de palabras actualmente registrados  
  
1.  Use la vista de catálogo [sys.fulltext_languages](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) , tal y como se muestra a continuación:  
  
    ```  
    SELECT * FROM sys.fulltext_languages;   
    ```  
  
### <a name="to-view-a-list-of-the-filters-that-are-currently-registered"></a>Para ver una lista de los filtros actualmente registrados  
  
1.  Use el procedimiento almacenado del sistema [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) , tal y como se muestra a continuación:  
  
    ```  
    EXEC sp_help_fulltext_system_components 'filter';    
    ```  
  
### <a name="to-register-newly-installed-word-breakers-and-filters"></a>Para registrar filtros y separadores de palabras recién instalados  
  
1.  Use el procedimiento almacenado del sistema [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql) para actualizar la lista de idiomas, tal y como se muestra a continuación:  
  
    ```  
    exec sp_fulltext_service 'update_languages';   
    ```  
  
### <a name="to-unregister-uninstalled-word-breakers-and-filters"></a>Para anular el registro de filtros y separadores de palabras instalados  
  
1.  Use **sp_fulltext_service** para actualizar la lista de idiomas, tal y como se muestra a continuación:  
  
    ```  
    exec sp_fulltext_service 'update_languages'  
    ```  
  
2.  Use **sp_fulltext_service** para reiniciar los procesos de host de demonio de filtro (fdhost.exe), tal y como se muestra a continuación:  
  
    ```  
    exec sp_fulltext_service 'restart_all_fdhosts';  
    ```  
  
### <a name="to-replace-existing-word-breakers-or-filters-when-installing-new-ones"></a>Para reemplazar los filtros o separadores de palabras existentes al instalar filtros o separadores de palabras nuevos  
  
1.  Cuando se prepare para instalar un archivo DLL que contenga nuevos filtros o separadores de palabras, compruebe que tenga un nombre de archivo distinto de cualquiera de los archivos DLL existentes instalados en su instancia del servidor.  
  
2.  Copie el nuevo archivo DLL en el directorio que contiene los archivos DLL estándar de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para la instancia del servidor. La ubicación predeterminada es:  
  
     C:\Archivos de programa\Microsoft SQL Server\MSSQL.*nombre_instancia*\MSSQL\Binn  
  
    > [!IMPORTANT]  
    >  Se recomienda encarecidamente que solamente cargue componentes firmados y comprobados. También se recomienda que ejecute el servicio del iniciador de FDHOST (MSSQLFDLauncher) con la menor cantidad de privilegios posible.  
  
3.  Instale los nuevos filtros o separadores de palabras.  
  
     **Para instalar y cargar IFilters de Microsoft Filter Pack**  
  
    -   [Cómo registrar IFilters de Microsoft Filter Pack con SQL Server](https://go.microsoft.com/fwlink/?LinkId=130439)  
  
4.  Use **sp_fulltext_service** para cargar los filtros y separadores de palabras recién instalados en la instancia del servidor, tal y como se muestra a continuación:  
  
    ```  
    EXEC sp_fulltext_service @action='load_os_resources', @value=1;  
    ```  
  
5.  Use **sp_fulltext_service** para actualizar la lista de idiomas, tal y como se muestra a continuación:  
  
    ```  
    EXEC sp_fulltext_service 'update_languages';  
    ```  
  
6.  Reinicie los procesos de host de demonio de filtro (fdhost.exe) mediante **sp_fulltext_service** , tal y como se muestra a continuación:  
  
    ```  
    EXEC sp_fulltext_service 'restart_all_fdhosts';   
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Establecer la cuenta del servicio para el selector del demonio de filtro completo](set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [Configurar y administrar filtros para búsquedas](configure-and-manage-filters-for-search.md)   
 [Configurar y administrar separadores de palabras y lematizadores para la búsqueda](configure-and-manage-word-breakers-and-stemmers-for-search.md)  
  
  
