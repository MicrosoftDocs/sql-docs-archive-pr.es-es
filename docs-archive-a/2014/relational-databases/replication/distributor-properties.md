---
title: Propiedades del distribuidor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distdbproperties.f1
- sql12.rep.configdistwizard.distproperties.general.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
- sql12.rep.configdistwizard.distproperties.publishers.f1
ms.assetid: f643c7c3-f238-4835-b81e-2c2b3b53b23f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 501c7931d651498fea49749be38af374c02424ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663381"
---
# <a name="sql-server-replication-distributor-properties"></a>Propiedades del distribuidor de Replicación de SQL Server
En este tema se describen las propiedades que se encuentran en las páginas **General**, **publicadores**y **base de datos de distribución** dentro de la ventana Propiedades del **distribuidor** . 

## <a name="general"></a>General
  La página **General** del cuadro de diálogo **Propiedades del distribuidor** le permite agregar y eliminar bases de datos de distribución y configurar las propiedades de la base de datos de distribución.  
  
 En la base de datos de distribución se almacenan metadatos y datos del historial de todos los tipos de replicación y transacciones de replicación transaccional. En muchas ocasiones, una sola base de datos de distribución resulta suficiente. Pero si varios publicadores utilizan un único distribuidor, podría ser aconsejable crear una base de datos de distribución para cada publicador. De esta forma, se garantiza que los datos que pasan por cada base de datos de distribución son distintos.  
  
### <a name="options"></a>Opciones  
 **Bases de datos**  
 La cuadrícula de propiedades de **Bases de datos** muestra el nombre y las propiedades de retención de las bases de datos del distribuidor. **Retención de transacción** representa el tiempo de almacenamiento de las transacciones de replicación transaccional (la retención de transacción también se denomina retención de distribución). **Retención de historial** representa el tiempo de almacenamiento de los metadatos del historial de todos los tipos de replicación. Para más información sobre la retención de la distribución, vea [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md) (Expiración y desactivación de la suscripción).  
  
 Haga clic en el botón de propiedades ( **...** ) en la cuadrícula de propiedades de **Bases de datos** para abrir el cuadro de diálogo **Propiedades de base de datos de distribución** .  
  
 **Nuevo**  
 Haga clic para crear una nueva base de datos de distribución.  
  
 **Eliminar**  
 Para eliminar una base de datos, seleccione una base de datos de distribución existente en la cuadrícula de propiedades de **Bases de datos** y haga clic en **Eliminar** . No puede eliminar la base de datos de distribución si solo existe dicha base de datos; cada distribuidor debe poseer al menos una base de datos de distribución. Para eliminar todas las bases de datos de distribución, deberá deshabilitar la distribución en el equipo. Para obtener más información, vea [Deshabilitar la publicación y distribución](disable-publishing-and-distribution.md).  
  
 **Valores predeterminados de perfil**  
 Haga clic para tener acceso a los perfiles del agente de replicación en el cuadro de diálogo **Perfiles de agente** . Para obtener más información acerca de los perfiles, vea [Replication Agent Profiles](agents/replication-agent-profiles.md).  

## <a name="publishers"></a>Publicadores

  La página **Publicadores** del cuadro de diálogo **Propiedades del distribuidor** permite habilitar a los publicadores para que puedan utilizar este distribuidor. También se pueden establecer propiedades asociadas con esos publicadores. Tenga en cuenta que permitir que un publicador utilice este servidor como su distribuidor remoto no hace que ese servidor sea un publicador. Debe conectarse al publicador, configurarlo para publicación y elegir este servidor como el distribuidor. Con el Asistente para nueva publicación puede configurar el publicador y elegir un distribuidor.  
  
### <a name="options"></a>Opciones  
 **Publicadores**  
 Seleccione los servidores que pueden utilizar este distribuidor. Haga clic en el botón **(...)** de Propiedades que se encuentra junto a un publicador para ver y establecer propiedades adicionales.  
  
 **Add**  
 Si el servidor que quiere habilitar no aparece, haga clic en **Agregar** para agregar un publicador de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un publicador de Oracle a la lista de publicadores disponibles. Si el servidor que agrega es el primer servidor que utilizará este distribuidor como distribuidor remoto, se le solicitará que proporcione una contraseña de vínculo administrativo.  
  
 **Contraseña de vínculo administrativo**  
 Use esta opción para especificar o actualizar la contraseña para la conexión que hace la replicación entre el publicador y el distribuidor remoto con el inicio de sesión **distributor_admin** :  
  
-   Si el distribuidor solo sirve a un distribuidor local, esta contraseña se genera de forma aleatoria y se configura automáticamente.  
-   Si el distribuidor ya tiene un publicador remoto, ello indica que inicialmente se ha suministrado una contraseña en esta página o en la página **Contraseña del distribuidor** del Asistente para configurar la distribución.    
-   Si habilita el primer publicador remoto para este distribuidor, se le solicitará que escriba una contraseña.  
  
 Para más información acerca de la seguridad para Distribuidores, vea [Proteger el distribuidor](security/secure-the-distributor.md).  

## <a name="distribution-database"></a>Base de datos de distribución
  El cuadro de diálogo **Propiedades de base de datos de distribución** permite ver un número de propiedades y establecer el período de retención de transacción y retención de historial para la base de datos.  
  
### <a name="options"></a>Opciones  
 **Nombre**  
 Nombre de la base de datos de distribución que, de manera predeterminada, se establece 'distribución' (de solo lectura).  
  
 **Ubicaciones de archivo**  
 Ubicación del archivo de la base de datos y del archivo de registro (de solo lectura).  
  
 **Período de retención de transacción**  
 También se conoce como período de retención de distribución. Representa el tiempo durante el cual se almacenan las transacciones para la replicación transaccional. Para más información, consulte [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 **Período de retención del historial**  
 Representa el tiempo durante el cual se almacenan los metadatos de historial para todos los tipos de replicación.  
  
 **Seguridad de Agente de lectura de cola**  
 El Agente de lectura de cola se utiliza con la replicación transaccional que admite suscripciones de actualización en cola. El Agente de lectura de cola se crea automáticamente si selecciona **Publicación transaccional con suscripciones actualizables** en la página **Tipo de publicación** del Asistente para nueva publicación. Haga clic en **Configuración de seguridad...** para cambiar la cuenta con la que el agente se ejecuta y establece conexiones con el distribuidor.  
  
 También se puede crear un Agente de lectura de cola seleccionando **Crear Agente de lectura de cola** en esta página (esta opción está deshabilitada si ya se ha creado el agente).  
  
 Puede encontrar más información de conexión para el Agente de lectura de cola en dos lugares:    
-   El agente se conecta al publicador con las credenciales especificadas en el cuadro de diálogo **Propiedades del publicador** , que se encuentra en la página **Publicadores** del cuadro de diálogo **Propiedades del distribuidor** .    
-   El agente se conecta con el suscriptor utilizando las credenciales especificadas para el Agente de distribución del Asistente para nueva suscripción.  
  
 Para obtener más información, consulte \\ [Replication Agent Security Model](security/replication-agent-security-model.md). 

  
## <a name="see-also"></a>Consulte también  
 [Configurar distribución](configure-distribution.md)   
 [Ver y modificar las propiedades del distribuidor y del publicador](view-and-modify-distributor-and-publisher-properties.md)   

  
  
