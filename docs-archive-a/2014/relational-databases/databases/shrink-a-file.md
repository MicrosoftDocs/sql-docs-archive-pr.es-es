---
title: Reducir un archivo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.shrinkfile.f1
helpviewer_keywords:
- shrinking files
- decreasing file size
- databases [SQL Server], shrinking
- reducing file size
- size [SQL Server], files
- file size [SQL Server]
ms.assetid: ce5c8798-c039-4ab2-81e7-90a8d688b893
author: stevestein
ms.author: sstein
ms.openlocfilehash: ac69e4bd2db3ef7fe0815d235dd1de7d3396b302
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87744122"
---
# <a name="shrink-a-file"></a>Reducir un archivo
  En este tema se describe cómo reducir un archivo de datos o de registro en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 La reducción de los archivos de datos permite recuperar espacio moviendo páginas de datos del final del archivo a espacio desocupado próximo al principio del archivo. Cuando se crea suficiente espacio disponible al final del archivo, las páginas de datos situadas al final del mismo se pueden desasignar y devolver al sistema de archivos.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Recomendaciones](#Recommendations)  
  
     [Seguridad](#Security)  
  
-   **Para reducir un archivo de datos o de registro, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitaciones y restricciones  
  
-   El archivo de datos principal no puede reducirse a un tamaño menor que el del archivo principal de la base de datos model.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recomendaciones  
  
-   Los datos que se mueven para reducir un archivo se pueden dispersar en cualquier ubicación disponible en el archivo. Esto produce la fragmentación de índices y puede reducir el rendimiento de las consultas que buscan un intervalo del índice. Para eliminar la fragmentación, considere la posibilidad de volver a generar los índices en el archivo después de la reducción.  
  
###  <a name="security"></a><a name="Security"></a> Seguridad  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permisos  
 Debe pertenecer al rol fijo de servidor **sysadmin** o al rol fijo de base de datos **db_owner** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Uso de SQL Server Management Studio  
  
#### <a name="to-shrink-a-data-or-log-file"></a>Para reducir un archivo de datos o de registro  
  
1.  En el Explorador de objetos, conéctese a una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] y expándala.  
  
2.  Expanda **Bases de datos** y, después, haga clic con el botón derecho en la base de datos que quiera reducir.  
  
3.  Seleccione **Tareas**y **Reducir**y haga clic en **Archivos**.  
  
     **Base de datos**  
     Muestra el nombre de la base de datos seleccionada.  
  
     **Tipo de archivo**  
     Seleccione el tipo de archivo. Las opciones disponibles son **Datos** y **Registro** . El valor predeterminado es **Datos**. Si se selecciona un tipo de grupo de archivos diferente, la selección de los demás campos también cambia.  
  
     **Grupo de archivos**  
     Seleccione un grupo de archivos en la lista de grupos de archivos asociados al **Tipo de archivo** seleccionado anteriormente. Si se selecciona un grupo de archivos diferente, la selección de los demás campos también cambia.  
  
     **Nombre de archivo**  
     Elija un archivo en la lista de archivos disponibles del grupo de archivos y del tipo de archivo seleccionados.  
  
     **Ubicación**  
     Muestra la ruta de acceso completa al archivo seleccionado. La ruta no se puede editar, pero se puede copiar al Portapapeles.  
  
     **Espacio asignado actualmente**  
     Para los archivos de datos, muestra el espacio asignado actualmente. En los archivos de registro, muestra el espacio asignado, calculado a partir del resultado de DBCC SQLPERF(LOGSPACE).  
  
     **Espacio disponible**  
     En los archivos de datos, muestra el espacio disponible, calculado a partir del resultado de DBCC SHOWFILESTATS(fileid). En los archivos de registro, muestra el espacio disponible, calculado a partir del resultado de DBCC SQLPERF(LOGSPACE).  
  
     **Liberar espacio no utilizado**  
     Hace que se libere el espacio no utilizado de los archivos para el sistema operativo y reduce el archivo a la última extensión asignada, lo que disminuye el tamaño del archivo sin mover los datos. No se realiza ningún intento de reubicación de las filas en páginas no asignadas.  
  
     **Reorganizar páginas antes de liberar espacio no utilizado**  
     Equivale a ejecutar DBCC SHRINKFILE con la especificación del tamaño del archivo de destino. Si se selecciona esta opción, el usuario debe especificar el tamaño del archivo de destino en el cuadro **Reducir el archivo a** .  
  
     **Reducir el archivo a**  
     Especifica el tamaño del archivo de destino para la operación de reducción. El tamaño no puede ser inferior al espacio asignado actual ni superior a la extensión total asignada al archivo. Si se introduce un valor inferior al mínimo o superior al máximo, se restablecerá el valor mínimo o máximo cuando cambie el foco o cuando se haga clic en los botones de la barra de herramientas.  
  
     **Vaciar el archivo migrando los datos a otros archivos del mismo grupo de archivos**  
     Migra todos los datos del archivo especificado. Esta opción permite que el archivo se pueda quitar mediante la instrucción ALTER DATABASE. Esta opción equivale a ejecutar DBCC SHRINKFILE con la opción EMPTYFILE.  
  
4.  Seleccione el tipo y el nombre del archivo.  
  
5.  También puede activar la casilla **Liberar espacio no utilizado** .  
  
     Si activa esta opción, el espacio no utilizado del archivo se libera al sistema operativo y el archivo se reduce a la última extensión asignada. De esta forma, se reduce el tamaño del archivo sin necesidad de mover datos.  
  
6.  También puede seleccionar la casilla **Reorganizar archivos antes de liberar espacio no utilizado** . Si activa esta opción, debe especificar el valor **Reducir el archivo a** . De forma predeterminada, esta opción no está activada.  
  
     Si activa esta opción, el espacio no utilizado del archivo se libera al sistema operativo y se intentan reubicar las filas en páginas no asignadas.  
  
7.  De manera opcional, especifique el porcentaje máximo de espacio disponible que desee dejar en el archivo de la base de datos después de reducirla. Los valores válidos están comprendidos entre 0 y 99. Esta opción solo está disponible cuando la opción **Reorganizar archivos antes de liberar espacio no utilizado** está habilitada.  
  
8.  De manera opcional, active la casilla **Vaciar el archivo migrando los datos a otros archivos del mismo grupo de archivos** .  
  
     Si activa esta opción, los datos se mueven del archivo especificado a otros archivos del grupo de archivos. A continuación, el archivo vacío puede eliminarse. Esta opción equivale a ejecutar DBCC SHRINKFILE con la opción EMPTYFILE.  
  
9. Haga clic en **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-shrink-a-data-or-log-file"></a>Para reducir un archivo de datos o de registro  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. Este ejemplo usa [DBCC SHRINKFILE](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql) para reducir a 7 MB el tamaño de un archivo de datos denominado `DataFile1` de la base de datos `UserDB` .  
  
 [!code-sql[DBCC#DBCC_SHRINKFILE1](../../snippets/tsql/SQL14/tsql/dbcc/transact-sql/dbcc_other.sql#dbcc_shrinkfile1)]  
  
## <a name="see-also"></a>Consulte también  
 [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)   
 [Reducir una base de datos](shrink-a-database.md)   
 [Eliminar archivos de datos o de registro de una base de datos](delete-data-or-log-files-from-a-database.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)  
  
  
