---
title: Inicializar una suscripción con una instantánea | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8b776e71e9d1197bc174169aee8ccf692884308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663348"
---
# <a name="initialize-a-subscription-with-a-snapshot"></a>Inicializar una suscripción con una instantánea
  Una vez que se ha creado una publicación, normalmente se crea una instantánea inicial, que se copia en la carpeta de instantáneas (es así de manera predeterminada para las publicaciones de combinación creadas con el Asistente para nueva publicación. A continuación, el Agente de distribución (para las publicaciones transaccionales y de instantáneas) o el Agente de mezcla (para las publicaciones de combinación) la aplican al suscriptor durante la sincronización inicial de la suscripción. El proceso de la instantánea depende del tipo de publicación:  
  
-   Si la instantánea es para una publicación de instantáneas, una publicación transaccional o una publicación de combinación que no utiliza filtros con parámetros, contiene el esquema y los datos en archivos de programa de copia masiva (bcp), así como las restricciones, las propiedades extendidas, los índices, los desencadenadores y las tablas del sistema que se necesitan para la replicación. Para más información acerca de la creación y aplicación de la instantánea, vea [Crear y aplicar una instantánea](create-and-apply-the-snapshot.md).  
  
-   Si la instantánea es para una publicación de combinación que utiliza filtros con parámetros, se crea mediante un proceso de dos partes. En primer lugar se crea una instantánea del esquema que contiene los scripts y el esquema de replicación de los objetos publicados, pero no los datos. A continuación, cada suscripción se inicializa con una instantánea que incluye los scripts y el esquema copiados de la instantánea de esquema y los datos que pertenecen a la partición de la suscripción. Para más información, consulte [Instantáneas para publicaciones de combinación con filtros con parámetros](snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 La instantánea se compone de varios archivos, según el tipo de replicación y los artículos de la publicación. Estos archivos se copian en la carpeta de instantáneas predeterminada especificada al configurar el distribuidor o en la carpeta alternativa especificada al crear la publicación.  
  
|Tipo de replicación|Archivos comunes de instantánea|  
|-------------------------|---------------------------|  
|Replicación de instantáneas o replicación transaccional|Esquemas (.sch), datos (.bcp), índices y restricciones (.dri), restricciones (.idx), desencadenadores (.trg) solo para actualizar suscriptores, archivos de instantáneas comprimidos (.cab).|  
|Replicación de mezcla|Esquemas (.sch), datos (.bcp), índices y restricciones (.dri), desencadenadores (.trg), datos de tabla del sistema (.sys), tablas de conflictos (.cft), archivos de instantáneas comprimidos (.cab).|  
  
 Si la transferencia de la instantánea se interrumpe en algún momento, continuará inmediatamente y no se volverá a enviar ningún archivo que ya hubiera sido transferido en su totalidad. La unidad de entrega del Agente de instantáneas es el archivo bcp de cada artículo de la publicación, de modo que los archivos entregados parcialmente deben volverse a entregar completamente. No obstante, continuar con la instantánea puede reducir de forma significativa la cantidad de datos transmitidos y garantizar una entrega a tiempo de la instantánea aunque la conexión no sea de confianza.  
  
## <a name="snapshot-options"></a>Opciones de instantánea  
 Hay una serie de opciones disponibles al inicializar una suscripción con una instantánea. Puede:  
  
-   Especificar una ubicación alternativa para la carpeta de instantáneas en lugar de, o además de, la predeterminada. Para más información, consulte [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md).  
  
-   Comprimir instantáneas para su almacenamiento en medios extraíbles o para su transferencia a través de una red lenta. Para más información, consulte [Compressed Snapshots](compressed-snapshots.md).  
  
-   Ejecutar scripts Transact-SQL antes o después de aplicar la instantánea. Para obtener más información, consulte [Ejecutar scripts antes y después de aplicar la instantánea](snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).  
  
-   Transferir la instantánea mediante el Protocolo de transferencia de archivos (FTP). Para obtener más información, vea [Transferir instantáneas mediante FTP](transfer-snapshots-through-ftp.md).  
  
## <a name="see-also"></a>Consulte también  
 [Initialize a Subscription](initialize-a-subscription.md)  (Inicializar una suscripción)  
 [Proteger la carpeta de instantáneas](security/secure-the-snapshot-folder.md)  
  
  
