---
title: Opción Preprocess (herramienta de administración de Distributed Replay) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7f168d45b03473d958e202bd75116f4519d2fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87670725"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a>Opción de preprocesamiento (herramienta de administración Distributed Replay)
  La [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herramienta de administración de Distributed Replay, `DReplay.exe` , es una herramienta de línea de comandos que puede usar para comunicarse con el controlador de reproducción distribuida. En este tema se describen la opción del símbolo del sistema **preprocess** y la sintaxis correspondiente.

 La opción **preprocess** inicia la fase de preprocesamiento. Durante esta fase, el controlador prepara los datos de seguimiento de entrada para la reproducción en el servidor destino.

 ![Icono de vínculo de tema](../../database-engine/media/topic-link.gif "Icono de vínculo de tema") Para más información sobre las convenciones de sintaxis que se usan con la sintaxis de la herramienta de administración, consulte [Convenciones de sintaxis de Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Sintaxis

```

      dreplay preprocess [-mcontroller] -iinput_trace_file
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]
```

#### <a name="parameters"></a>Parámetros
 *controlador* **-m** especifica el nombre del equipo del controlador. Puede utilizar "`localhost`" o "`.`" para hacer referencia al equipo local.

 Si no se especifica el parámetro **-m** , se usará el equipo local.

 **-i** *input_trace_file* especifica la ruta de acceso completa del archivo de seguimiento de entrada en el controlador, como `D:\Mytrace.trc` . El parámetro **-i** es obligatorio.

 Si hay archivos de sustitución incremental en el mismo directorio, se cargarán y usarán automáticamente. Los archivos deben seguir la convención de nomenclatura de sustitución incremental de archivos, por ejemplo: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`... `Mytrace_n.trc`.

> [!NOTE]
>  Si está usando la herramienta de administración en un equipo que no es el controlador, tendrá que copiar los archivos de seguimiento de entrada en el controlador de forma que se pueda usar una ruta de acceso local para este parámetro.

 **-d** *controller_working_dir* especifica el directorio del controlador donde se almacenará el archivo intermedio. El parámetro **-d** es obligatorio.

 Se aplican los siguientes requisitos:

-   El directorio debe residir en el controlador.

-   Debe especificar la ruta de acceso completa, comenzando por una letra de unidad (por ejemplo, `c:\WorkingDir`).

-   La ruta de acceso no debe finalizar con una barra diagonal inversa "`\`".

-   No se admiten las rutas de acceso UNC.

 **-c** *config_file* es la ruta de acceso completa del archivo de configuración de preprocesamiento; se usa para especificar la ubicación del archivo de configuración de preprocesamiento cuando se almacena en una ubicación diferente. Este parámetro puede ser una ruta UNC o puede residir localmente en el equipo donde se ejecuta la herramienta de administración.

 El parámetro **-c** no es obligatorio si no se necesita ningún filtrado o si no se quiere modificar el tiempo de inactividad máximo.

 Sin el parámetro **-c** , se usa el archivo de configuración de preprocesamiento predeterminado, `DReplay.exe.preprocess.config`.

 **-f** *status_interval* especifica la frecuencia (en segundos) con la que se muestran los mensajes de estado.

 Si no se especifica **-f** , el intervalo predeterminado es de 30 segundos.

## <a name="examples"></a>Ejemplos
 En este ejemplo, la copia intermedia del preprocesamiento se inicia con toda la configuración predeterminada. El valor `localhost` indica que el servicio del controlador se está ejecutando en el mismo equipo que la herramienta de administración. El parámetro *input_trace_file* especifica la ubicación de los datos de seguimiento de entrada, `c:\mytrace.trc`. Dado que no se usa ningún filtrado de archivos de seguimiento, no es necesario especificar el parámetro **-c** .

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir
```

 En este ejemplo, se inicia la fase de preprocesamiento y se especifica un archivo de configuración del preprocesamiento modificado. A diferencia del ejemplo anterior, el parámetro **-c** se usa para indicar el archivo de configuración modificado, si se ha almacenado en otra ubicación. Por ejemplo:

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config
```

 En el archivo de configuración del preprocesamiento modificado, se agrega una condición de filtro que deja fuera las sesiones del sistema durante la reproducción distribuida. El filtro se agrega modificando el elemento `<PreprocessModifiers>` del archivo de configuración del preprocesamiento, `DReplay.exe.preprocess.config`.

 En el ejemplo siguiente se muestra un ejemplo del archivo de configuración modificado:

```
<?xml version='1.0'?>
<Options>
    <PreprocessModifiers>
        <IncSystemSession>No</IncSystemSession>
        <MaxIdleTime>-1</MaxIdleTime>
    </PreprocessModifiers>
</Options>
```

## <a name="permissions"></a>Permisos
 Debe ejecutar la herramienta de administración como un usuario interactivo, como un usuario local o una cuenta de usuario de dominio. Para utilizar una cuenta de usuario local, la herramienta de administración y el controlador se deben estar ejecutando en el mismo equipo.

 Para más información, consulte [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>Consulte también
 [Preparar los datos de seguimiento de entrada](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [configurar Distributed Replay](configure-distributed-replay.md)


