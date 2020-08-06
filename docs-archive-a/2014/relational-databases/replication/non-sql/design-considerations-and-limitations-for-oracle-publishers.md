---
title: Consideraciones y limitaciones de diseño de los publicadores de Oracle | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], design considerations and limitations
ms.assetid: 8d9dcc59-3de8-4d36-a61f-bc3ca96516b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b2776452e0da93cb1f170b6ee3356d95158df6b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87748056"
---
# <a name="design-considerations-and-limitations-for-oracle-publishers"></a>Consideraciones y limitaciones de diseño de los publicadores de Oracle
  La publicación desde una base de datos de Oracle está diseñada para funcionar casi igual que la publicación desde una [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de datos. No obstante, debe tener en cuenta las siguientes limitaciones y problemas:  
  
-   La opción de puerta de enlace de Oracle proporciona mejor rendimiento que la opción Completo. No obstante, esta opción no se puede utilizar para publicar la misma tabla en varias publicaciones transaccionales. Una tabla puede aparecer como máximo en una publicación transaccional y en cualquier número de publicaciones de instantánea. Si necesita publicar la misma tabla en varias publicaciones transaccionales, elija la opción Completo de Oracle.  
  
-   La replicación admite la publicación de tablas, índices y vistas materializadas. No se replican otros objetos.  
  
-   Existen pequeñas diferencias entre el almacenamiento y el procesamiento de datos en Oracle y las bases de datos de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que afectan a la replicación.  
  
-   Existen ciertas diferencias en el modo en que se admiten las características de replicación transaccional al utilizar un publicador de Oracle.  
  
## <a name="support-for-publishing-objects-from-oracle"></a>Compatibilidad con objetos de publicación de Oracle  
 La replicación admite los siguientes objetos de las bases de datos de Oracle:  
  
-   Tablas  
  
-   Tablas organizadas por índices  
  
-   Índices  
  
-   Vistas materializadas (se replican como tablas)  
  
 Los siguientes elementos pueden aparecer en tablas publicadas pero no se replican:  
  
-   Índices basados en dominios  
  
-   Índices basados en funciones  
  
-   Valores predeterminados  
  
-   Restricciones CHECK  
  
-   Claves externas  
  
-   Opciones de almacenamiento (espacios de tabla, clústeres, etc.)  
  
 No es posible replicar los siguientes objetos:  
  
-   Tablas anidadas  
  
-   Vistas  
  
-   Paquetes, cuerpos de paquetes, procedimientos y desencadenadores  
  
-   Colas  
  
-   Secuencias  
  
-   Sinónimos  
  
 Para obtener información acerca de los tipos de datos admitidos, vea [Data Type Mapping for Oracle Publishers](data-type-mapping-for-oracle-publishers.md).  
  
## <a name="differences-between-oracle-and-sql-server"></a>Diferencias entre Oracle y SQL Server  
  
-   Oracle tiene límites de tamaño máximo diferentes para algunos objetos. Cualquier objeto creado en la base de datos de publicación de Oracle debe respetar los límites de tamaño máximo de los correspondientes objetos en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Para más información, sobre los límites de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vea [Maximum Capacity Specifications for SQL Server](../../../sql-server/maximum-capacity-specifications-for-sql-server.md) (Especificaciones de capacidad máxima para SQL Server).  
  
-   Los nombres de objeto de Oracle se crean de manera predeterminada en mayúsculas. Asegúrese de proporcionar los nombres de los objetos de Oracle en mayúsculas al publicarlos a través de un distribuidor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] si están en mayúsculas en la base de datos de Oracle. Si no se especifican los objetos en mayúsculas o minúsculas correctamente, se puede producir un mensaje de error que indica que no se puede encontrar el objeto.  
  
-   Oracle tiene un dialecto SQL ligeramente diferente de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; los filtros de fila se deben escribir en sintaxis compatible con Oracle.  
  
### <a name="considerations-for-large-objects"></a>Consideraciones para objetos grandes  
 Los datos de objetos grandes (LOB) no se almacenan en la tabla de registro de artículos; las actualizaciones de datos LOB se recuperan directamente en la tabla publicada. Las actualizaciones se replican en publicaciones transaccionales solamente si la operación que afecta al LOB activa el desencadenador de replicación en la tabla replicada. Los desencadenadores de Oracle se activan cuando se insertan o eliminan filas que contienen LOB; sin embargo, las actualizaciones de columnas LOB no activan los desencadenadores. Una actualización de una columna LOB se replicará inmediatamente solo si una columna no LOB de la misma fila se actualiza también en la misma transacción de Oracle. Si no, la columna LOB se actualizará en el suscriptor cuando se produzca la siguiente actualización de una columna no LOB de la misma fila. Asegúrese de que este comportamiento es aceptable para su aplicación.  
  
 Para replicar actualizaciones de columnas LOB en publicaciones transaccionales, considere una de las siguientes estrategias cuando escriba la aplicación:  
  
-   Elimine y vuelva a insertar las filas en una transacción en lugar de actualizar la fila: especifique el nuevo LOB al volver a insertar la fila. Como la eliminación y la inserción activan desencadenadores, la fila se replicará.  
  
-   Incluya una columna no LOB en la actualización de filas además de la columna LOB, o actualice una columna no LOB de la fila como parte de la misma transacción de Oracle. En ambos casos, la actualización de la columna no LOB garantiza que se active el desencadenador.  
  
 Para obtener más información sobre los LOB, vea [Data Type Mapping for Oracle Publishers](data-type-mapping-for-oracle-publishers.md).  
  
### <a name="unique-indexes-and-constraints"></a>Índices y restricciones únicos  
 En la replicación de instantáneas y transaccional, las columnas contenidas en índices y restricciones únicos (incluidas las restricciones de clave principal) deben respetar ciertas limitaciones Si no se respetan dichas limitaciones, la restricción o el índice no se replican.  
  
-   El número máximo de columnas permitido en un índice en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] es de 16.  
  
-   Todas las columnas incluidas en restricciones únicas deben tener tipos de datos admitidos. Para obtener más información acerca de los tipos de datos, vea [Data Type Mapping for Oracle Publishers](data-type-mapping-for-oracle-publishers.md).  
  
-   Todas las columnas incluidas en restricciones únicas se deben publicar (no se pueden filtrar).  
  
-   Las columnas incluidas en restricciones o índices únicos no deben ser de tipo NULL.  
  
 Considere también los siguientes problemas:  
  
-   Oracle y [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tratan NULL de manera diferente: Oracle admite varias filas con valores NULL para las columnas que permiten NULL y se incluyen en restricciones o índices únicos. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aplica la singularidad solo permitiendo una única fila con un valor NULL para la misma columna. No puede publicar un índice o restricción únicos que permita el valor NULL porque se produciría una infracción de restricción en el suscriptor si la tabla publicada contiene varias filas con valores NULL para cualquiera de las columnas incluidas en el índice o restricción.  
  
-   Al probar la unicidad, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] omite los espacios en blanco de un campo pero Oracle no.  
  
 Como en la replicación transaccional de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , las tablas de las publicaciones transaccionales de Oracle requieren una clave principal, que debe ser única según las reglas especificadas anteriormente. Si la clave principal no sigue las reglas indicadas anteriormente, no se puede publicar la tabla para la replicación transaccional.  
  
## <a name="differences-between-oracle-publishing-and-standard-transactional-replication"></a>Diferencias entre la publicación de Oracle y la replicación transaccional estándar  
  
-   Un publicador de Oracle no puede tener el mismo nombre que su distribuidor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ni el mismo nombre que ninguno de los publicadores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que utilizan el mismo distribuidor, ni que ninguno de los suscriptores que reciben la publicación. Las publicaciones a las que da servicio el mismo distribuidor deben tener nombres únicos.  
  
-   Una tabla publicada en una publicación de Oracle no puede recibir datos replicados. Por eso, la publicación de Oracle no es compatible con publicaciones con suscripciones de actualización inmediata o de actualización en cola, ni con topologías en las que las tablas de publicación son a la vez tablas de suscripción, como la replicación punto a punto y bidireccional.  
  
-   Las relaciones de clave principal a clave externa de la base de datos de Oracle no se replican en los suscriptores. No obstante, se mantienen las relaciones en los datos cuando se entregan los cambios.  
  
-   Las publicaciones transaccionales estándar admiten tablas de hasta 1000 columnas. Las publicaciones transaccionales de Oracle admiten 995 columnas (la replicación agrega cinco columnas a cada tabla publicada).  
  
-   Se agregan cláusulas de intercalación a las instrucciones CREATE TABLE para habilitar las comparaciones que distinguen entre mayúsculas y minúsculas, que es importante para las claves principales y las restricciones únicas. Este comportamiento se controla con la opción de esquema 0x1000, que se especifica con el **@schema_option** parámetro de [sp_addarticle &#40;&#41;de TRANSACT-SQL ](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).  
  
-   Si utiliza procedimientos almacenados para configurar o mantener un publicador de Oracle, no coloque los procedimientos dentro de una transacción explícita. El servidor vinculado que se utiliza para conectar al publicador de Oracle no admite dicha transacción.  
  
-   Si crea una suscripción de extracción en una publicación de Oracle con un asistente, debe utilizar el Asistente para nueva suscripción con [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] y versiones posteriores. No obstante, para las versiones anteriores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], puede utilizar el procedimiento almacenado y las interfaces SQL-DMO para configurar suscripciones de extracción a publicaciones de Oracle.  
  
-   Si utiliza procedimientos almacenados para propagar los cambios a los suscriptores (valor predeterminado), tenga en cuenta que se admite la sintaxis MCALL, pero que su comportamiento es diferente cuando la publicación es de un publicador de Oracle. Normalmente MCALL proporciona un mapa de bits que muestra qué columnas se han actualizado en el publicador. Con una publicación de Oracle, el mapa de bits muestra siempre que todas las columnas han sido actualizadas. Para más información sobre el uso de procedimientos personalizados, vea [Especificar cómo se propagan los cambios para los artículos transaccionales](../transactional/transactional-articles-specify-how-changes-are-propagated.md).  
  
### <a name="transactional-replication-feature-support"></a>Compatibilidad con características de replicación transaccional  
  
-   Las publicaciones de Oracle no admiten todas las opciones de esquema que admiten las publicaciones de SQL Server. Para más información sobre las opciones de esquema, vea [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).  
  
-   Los suscriptores de publicaciones de Oracle no pueden utilizar suscripciones de actualización inmediata o de actualización en cola, ni ser nodos en una topología punto a punto o bidireccional.  
  
-   Los suscriptores de publicaciones de Oracle no se pueden inicializar automáticamente desde una copia de seguridad.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] admite dos tipos de validación: binaria y de recuento de filas. Los publicadores de Oracle admiten la validación de recuento de filas. Para obtener más información, vea [Validar datos replicados](../validate-data-at-the-subscriber.md).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] proporciona dos formatos de instantánea: modo bcp nativo y modo de carácter. Los publicadores de Oracle admiten las instantáneas en modo de carácter.  
  
-   No se admiten los cambios de esquema en las tablas de Oracle publicadas. Para realizar los cambios de esquema, quite primero la publicación, realice los cambios y vuelva a crear la publicación y todas las suscripciones.  
  
    > [!NOTE]  
    >  Si se realizan los cambios de esquema y la posterior eliminación y nueva creación de la publicación y las suscripciones cuando no se está produciendo ninguna actividad en las tablas publicadas, puede especificar la opción "solo compatibilidad con replicación" para las suscripciones. Esto les permite sincronizarse sin tener que copiar una instantánea en cada suscriptor. Para obtener más información, consulte [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).  
  
### <a name="replication-security-model"></a>Modelo de seguridad de replicación  
 El modelo de seguridad de la publicación de Oracle es el mismo que el de la replicación transaccional estándar, con las siguientes excepciones:  
  
-   La cuenta con la que el Agente de instantáneas y el Agente de registro del LOG realizan las conexiones del distribuidor al publicador se especifica mediante uno de los siguientes métodos:  
  
    -   **@security_mode**Parámetro de [sp_adddistpublisher &#40;&#41;de TRANSACT-SQL](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql) (también se especifican valores para **@login** y **@password** si se utiliza la autenticación de Oracle)  
  
    -   En el cuadro del diálogo **Conectar al servidor** en SQL Server Management Studio, que se utiliza al configurar el publicador de Oracle en el distribuidor de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
     En la replicación transaccional estándar, la cuenta se especifica con [sp_addpublication_snapshot &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) y [sp_addlogreader_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql).  
  
-   La cuenta con la que el Agente de instantáneas y el Agente de registro del LOG realizan las conexiones no se puede cambiar con [sp_changedistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) ni a través de una hoja de propiedades, pero se puede cambiar la contraseña.  
  
-   Si especifica un valor de 1 (autenticación integrada de Windows) para el **@security_mode** parámetro de [sp_adddistpublisher &#40;&#41;de TRANSACT-SQL ](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql):  
  
    -   La cuenta de proceso y la contraseña que se usan para el Agente de instantáneas y el Agente de registro del LOG (los **@job_login** **@job_password** parámetros y de [sp_addpublication_snapshot &#40;&#41;de Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql) y [sp_addlogreader_agent &#40;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql)) deben ser los mismos que la cuenta y la contraseña que se usan para conectarse al publicador de Oracle.  
  
    -   No se puede cambiar el **@job_login** parámetro a través de [sp_changepublication_snapshot &#40;&#41;de TRANSACT-sql](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql) o [SP_CHANGELOGREADER_AGENT &#40;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql)&#41;, pero se puede cambiar la contraseña.  
  
 Para obtener más información sobre la seguridad de la replicación, consulte [replicación de SQL Server Security](../security/view-and-modify-replication-security-settings.md).  
  
## <a name="see-also"></a>Consulte también  
 [Consideraciones administrativas para los publicadores de Oracle](administrative-considerations-for-oracle-publishers.md)   
 [Configurar un publicador de Oracle](configure-an-oracle-publisher.md)   
 [Información general de la publicación de Oracle](oracle-publishing-overview.md)  
  
  
