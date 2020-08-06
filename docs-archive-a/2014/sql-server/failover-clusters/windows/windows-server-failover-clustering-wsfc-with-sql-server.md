---
title: Clústeres de conmutación por error de Windows Server (WSFC), con SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Windows Server Failover Clustering (WSFC), with SQL Server
- WSFC, with SQL Server
- quorum [SQL Server]
- failover clustering [SQL Server], AlwaysOn Availability Groups
ms.assetid: 79d2ea5a-edd8-4b3b-9502-96202057b01a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1fec03d7eb7a63353fd8eaea8c1e7051a306049
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672547"
---
# <a name="windows-server-failover-clustering-wsfc-with-sql-server"></a>Clústeres de conmutación por error de Windows Server (WSFC) con SQL Server
  Un clúster de *clústeres de conmutación por error de Windows Server* (WSFC) es un grupo de servidores independientes que funcionan conjuntamente para aumentar la disponibilidad de aplicaciones y servicios. [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] aprovecha los servicios y las capacidades de WSFC para admitir instancias de clúster de conmutación por error de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] y [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .

 

##  <a name="terms-and-definitions"></a><a name="TermsAndDefs"></a> Términos y definiciones
 Clúster WSFC un clúster de clústeres de conmutación por error de Windows Server (WSFC) es un grupo de servidores independientes que funcionan conjuntamente para aumentar la disponibilidad de las aplicaciones y los servicios.

 Instancia de clúster de conmutación por error instancia de un servicio de Windows que administra un recurso de dirección IP, un recurso de nombre de red y recursos adicionales necesarios para ejecutar una o varias aplicaciones o servicios. Los clientes pueden utilizar el nombre de red para tener acceso a los recursos del grupo de modo similar a utilizar un nombre de equipo para tener acceso a los servicios en un servidor físico. Sin embargo, dado que una instancia de clúster de conmutación por error es un grupo, puede ser objeto de conmutación por error a otro nodo sin que se vean afectados el nombre o la dirección subyacentes.

 Nodo un sistema de Microsoft Windows Server que es miembro activo o inactivo de un clúster de servidores.

 Recurso de clúster una entidad física o lógica que puede ser propiedad de un nodo, poner en línea y desconectarse, moverse entre nodos y administrarse como un objeto de clúster. Un recurso de clúster puede ser propiedad de un único nodo en cualquier momento.

 Grupo de recursos una colección de recursos de clúster administrados como un único objeto de clúster. Normalmente, un grupo de recursos contiene todos los recursos de clúster necesarios para ejecutar una aplicación o un servicio específicos. La conmutación por error y la conmutación por recuperación siempre actúan en grupos de recursos.

 Dependencia de recursos de un recurso del que depende otro recurso. Si el recurso A depende del recurso B, B es una dependencia de A.

 Recurso de nombre de red un nombre de servidor lógico que se administra como un recurso de clúster. Un recurso de nombre de red debe utilizarse con un recurso de dirección IP.

 Propietario preferido: nodo en el que prefiere ejecutarse un grupo de recursos. Cada grupo de recursos está asociado a una lista de propietarios preferidos clasificados en orden de preferencia. Durante la conmutación por error automática, el grupo de recursos se pasa al nodo preferido siguiente en la lista de propietarios preferidos.

 Posible propietario un nodo secundario en el que se puede ejecutar un recurso. Cada grupo de recursos está asociado a una lista de posibles propietarios. Los grupos de recursos pueden ser objeto de conmutación por error solo en los nodos enumerados como posibles propietarios.

 Modo de cuórum la configuración de cuórum en un clúster de conmutación por error que determina el número de errores de nodo que el clúster puede admitir.

 Quórum forzado el proceso para iniciar el clúster aunque solo una minoría de los elementos necesarios para el cuórum esté en comunicación.

 Para obtener más información, vea el [Glosario de clústeres de conmutación por error](/previous-versions/windows/desktop/MsCS/server-cluster-glossary)

##  <a name="overview-of-windows-server-failover-clustering"></a><a name="Overview"></a> Información general de clústeres de conmutación por error de Windows Server
 Los clústeres de conmutación por error de Windows Server proporcionan características de infraestructura que admiten escenarios de alta disponibilidad y recuperación ante desastres de aplicaciones de servidor hospedadas, como Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y Microsoft Exchange. Si un nodo o un servicio de clúster tiene un error, los servicios hospedados en ese nodo se pueden transferir automática o manualmente a otro nodo disponible en un proceso denominado *conmutación por error*.

 Los nodos del clúster de WSFC trabajan juntos para proporcionar colectivamente estos tipos de funciones:

-   **Notificaciones y metadatos distribuidos.** El servicio de WSFC y lo metadatos de aplicaciones hospedadas se mantiene en cada nodo del clúster. Estos metadatos incluyen la configuración y el estado de WSFC además de la configuración de la aplicación hospedada. Los cambios en los metadatos o el estado de un nodo se propagan automáticamente a los demás nodos del clúster.

-   **Administración de recursos.** Los nodos individuales del clúster pueden proporcionar recursos físicos como almacenamiento asociado directo, interfaces de red y acceso al almacenamiento en disco compartido. Las aplicaciones hospedadas se registran como un recurso de clúster y pueden configurar dependencias de inicio y de estado en otros recursos.

-   **Seguimiento de estado.** La detección del estado del nodo principal y entre nodos se realiza mediante una combinación de comunicaciones de red de tipo latido y supervisión de recursos. Los votos de un quórum de nodos del clúster determinan el estado general del clúster.

-   **Coordinación de conmutación por error.** Cada uno de los recursos se configura para ser hospedado en un nodo principal y se pueden transferir automática o manualmente a uno o varios nodos secundarios. Una directiva de conmutación por error basada en el estado controla la transferencia automática de la propiedad de recursos entre los nodos. Los nodos y las aplicaciones hospedadas son informadas cuando se produce la conmutación por error para puedan reaccionar correctamente.

 Para obtener más información, vea el tema sobre [clústeres de conmutación por error en Windows Server 2008 R2](https://technet.microsoft.com/library/ff182338\(WS.10\).aspx)

##  <a name="sql-server-alwayson-technologies-and-wsfc"></a><a name="AlwaysOnWsfcTech"></a>Tecnologías de SQL Server AlwaysOn y WSFC
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]*AlwaysOn* es una nueva solución de alta disponibilidad y recuperación ante desastres que aprovecha las ventajas de WSFC. AlwaysOn proporciona una solución integrada y flexible que aumentar la disponibilidad de las aplicaciones, proporciona mejores réditos en inversiones de hardware y simplificar la implementación y administración de alta disponibilidad.

 Tanto las instancias de clúster de conmutación por error [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] como AlwaysOn usan WSFC como tecnología de plataforma, registrando los componentes como recursos de clúster de WSFC.  Los recursos relacionados se combinan en un *grupo de recursos*que pueden hacerse dependientes de otros recursos de clúster de WSFC. El servicio de clúster de WSFC puede detectar y designar la necesidad de reiniciar la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o realizar automáticamente la conmutación por error a otro nodo del servidor del clúster de WSFC.

> [!IMPORTANT]
>  Para aprovechar las tecnologías de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn, se deben aplicar varios requisitos previos relacionados con WSFC.
> 
>  Para obtener más información, vea: [requisitos previos, restricciones y recomendaciones para Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)

### <a name="instance-level-high-availability-with-alwayson-failover-cluster-instances"></a>Alta disponibilidad en el nivel de instancia con instancias de clúster de conmutación por error AlwaysOn
 Una *instancia de clúster de conmutación por error* (FCI) de AlwaysOn es una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que está instalada en los nodos de un clúster de conmutación por error de WSFC. Este tipo de instancia tiene dependencias de recursos en un almacenamiento en disco compartido (a través de canal de fibra o SAN iSCSI) y en un nombre de red virtual. El nombre de red virtual tiene una dependencia de recursos en una o más direcciones IP virtuales, cada una en una subred diferente. El servicio SQL Server y el servicio del Agente SQL Server se registran como recursos, y ambos se hacen dependientes del recurso de nombre de red virtual.

 En caso de conmutación por error, el servicio de WSFC transfiere la propiedad de los recursos de la instancia a un nodo de conmutación por error designado. La instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vuelve a iniciarse en el nodo de conmutación por error y las bases de datos se recuperan de la forma habitual. En cualquier momento determinado, solo un nodo del clúster puede hospedar la FCI y los recursos subyacentes.

> [!NOTE]
>  Una instancia de clúster de conmutación por error AlwaysOn requiere almacenamiento en disco compartido simétrico como una red de área de almacenamiento (SAN) o un recurso compartido de archivos SMB.  Los volúmenes de almacenamiento en disco compartido deben estar disponible para todos los nodos potenciales de conmutación por error en el clúster de WSFC.

 Para obtener más información, consulte: [instancias de clúster de conmutación por error de AlwaysOn](always-on-failover-cluster-instances-sql-server.md)

### <a name="database-level-high-availability-with-sshadr"></a>Alta disponibilidad en el nivel de base de datos con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]
 Un *grupo de disponibilidad* es un conjunto de bases de datos de usuario que realizan la conmutación por error conjuntamente. Un grupo de disponibilidad consta de una *réplica de disponibilidad* principal y de una a cuatro réplicas secundarias que se mantienen mediante el movimiento de datos basado en registros de SQL Server para la protección de datos sin necesidad de almacenamiento compartido. Cada réplica está hospedada en una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en otro nodo del clúster de WSFC. El grupo de disponibilidad y un nombre de red virtual correspondiente se registran como recursos del clúster de WSFC.

 Un *agente de escucha de grupo de disponibilidad* del nodo de la réplica principal responde a las solicitudes de cliente entrantes para conectarse al nombre de red virtual y, en función de los atributos de la cadena de conexión, redirige cada solicitud a la instancia adecuada de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .

 En el caso de una conmutación por error, en lugar de transferir la propiedad de los recursos físicos compartidos a otro nodo, WSFC aprovecha para volver a configurar una réplica secundaria en otra instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y que se convierta en la réplica principal del grupo de disponibilidad. El recurso de nombre de red virtual del grupo de disponibilidad se transfiere después a esa instancia.

 En cualquier momento dado, solo una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] puede hospedar la réplica principal de las bases de datos de un grupo de disponibilidad, todas las réplicas secundarias asociadas deben residir cada una en una instancia independiente, y cada instancia debe residir en nodos físicos distintos.

> [!NOTE]
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] no necesita la implementación de una instancia de clúster de conmutación por error ni el uso de almacenamiento compartido simétrico (SAN o SMB).
> 
>  Una instancia de clúster de conmutación por error (FCI) se puede usar junto con un grupo de disponibilidad para mejorar la disponibilidad de una réplica de disponibilidad. Sin embargo, para evitar posibles condiciones de carrera en el clúster de WSFC, la conmutación automática por error del grupo de disponibilidad no se admite en o desde una réplica de disponibilidad hospedada en una FCI.

 Para obtener más información, vea: [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).

##  <a name="wsfc-health-monitoring-and-failover"></a><a name="AlwaysOnWsfcHealth"></a>Supervisión de estado y conmutación por error de WSFC
 La alta disponibilidad para una solución de AlwaysOn se consigue mediante la supervisión de estado proactiva de los recursos de clúster de WSFC físicos y lógicos, junto con la conmutación por error automática y la reconfiguración de hardware redundante.  Un administrador del sistema también puede iniciar una *conmutación por error manual* de un grupo de disponibilidad o una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] entre nodos.

### <a name="failover-policies-for-nodes-failover-cluster-instances-and-availability-groups"></a>Directivas de conmutación por error para nodos, instancias de clúster de conmutación por error y grupos de disponibilidad
 Una *directiva de conmutación por error* se configura en los siguientes niveles: nodo de clúster de WSFC, instancia de clúster de conmutación por error (FCI) de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y grupo de disponibilidad.  Estas directivas, basadas en la gravedad, duración y frecuencia del estado incorrecto de los recursos de clúster y la capacidad de respuesta de los nodos, puede desencadenar el reinicio de un servicio o una *conmutación automática por error* de los recursos de clúster entre nodos, o puede desencadenar el paso de la réplica principal de un grupo de disponibilidad desde una instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a otra.

 La conmutación por error de la réplica de un grupo de disponibilidad no afecta a la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] subyacente.  La conmutación por error de una FCI mueve las réplicas hospedadas de grupo de disponibilidad con la instancia.

 Para obtener más información, consulte: [Directiva de conmutación por error para instancias de clúster de conmutación por error](failover-policy-for-failover-cluster-instances.md)

### <a name="wsfc-resource-health-detection"></a>Detección del estado de los recursos de WSFC
 Cada recurso de un nodo de clúster de WSFC puede notificar su condición y estado periódicamente o a petición. Una variedad de circunstancias puede indicar el error de recursos. Por ejemplo, una interrupción del suministro eléctrico, errores de disco o de memoria, errores de la comunicación de red o servicios que no responden.

 Los recursos de clúster de WSFC como redes, almacenamiento o servicios se pueden hacer dependientes unos de otros. El estado acumulativo de un recurso está determinado por la acumulación sucesiva de su condición con el estado de cada una de sus dependencias de recursos.

### <a name="wsfc-inter-node-health-detection-and-quorum-voting"></a>Detección del estado entre nodos de WSFC y votos de quórum
 Cada nodo de un clúster WSFC participa en la comunicación periódica de latido para compartir el estado de mantenimiento del nodo con los demás nodos. Los nodos que no responden se consideran que se encuentran en estado de error.

 Un conjunto de nodos de *quórum* es una mayoría de los nodos con derecho a voto y testigos en el clúster WSFC. Un *voto de quórum*periódico determina el estado general de un clúster WSFC. La presencia de un quórum significa que el clúster es correcto y puede proporcionar tolerancia a errores de nivel de nodo.

 En el nivel de clúster de WSFC se configura un *modo de quórum* que dicta la metodología empleada para los votos de quórum y cuándo se ha de realizar una conmutación por error automática o poner el clúster sin conexión.

> [!TIP]
>  Se recomienda tener siempre un número impar de votos de quórum en un clúster de WSFC.  A efectos de los votos de quórum, no es necesario que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esté instalado en todos los nodos del clúster. Un servidor adicional puede actuar como miembro de quórum, o el modelo de quórum de WSFC se puede configurar para que se use un recurso compartido de archivos remoto como factor de desempate.
> 
>  Para obtener más información, vea: [modos de cuórum de WSFC y configuración de votación &#40;SQL Server&#41;](wsfc-quorum-modes-and-voting-configuration-sql-server.md)

### <a name="disaster-recovery-through-forced-quorum"></a>Recuperación ante desastres mediante quórum forzado
 Dependiendo de las prácticas operativas y la configuración del clúster de WSFC, se puede incurrir en conmutaciones por error automáticas y manuales manteniendo al mismo tiempo una solución sólida y con tolerancia a errores de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn. Sin embargo, si un quórum de los nodos con derecho a voto del clúster de WSFC no puede comunicarse con otro, o si el clúster de WSFC tiene un error en la validación del estado, el clúster de WSFC puede pasar a estar sin conexión.

 Si el clúster de WSFC pasa a estar sin conexión debido a un desastre imprevisto o debido a un error persistente de hardware o de comunicaciones, se requiere la intervención manual administrativa para *forzar un cuórum* y poner de nuevo en línea los nodos de clúster supervivientes en una configuración sin tolerancia a errores.

 Posteriormente, también debe realizarse una serie de pasos para volver a configurar el clúster de WSFC, recuperar las réplicas de base de datos afectadas y restablecer un nuevo quórum.

 Para obtener más información, vea: [Recuperación ante desastres del clúster WSFC mediante cuórum forzado &#40;SQL Server&#41;](wsfc-disaster-recovery-through-forced-quorum-sql-server.md).

##  <a name="relationship-of-sql-server-alwayson-components-to-wsfc"></a><a name="AlwaysOnWsfcRelationship"></a> Relación de los componentes de SQL Server AlwaysOn con WSFC
 Existen varios niveles de relaciones entre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn y las características y los componentes de WSFC.

 Los grupos de disponibilidad AlwaysOn se hospedan en instancias de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .
Una solicitud de cliente que especifica un nombre de red de agente de escucha del grupo de disponibilidad lógico para conectarse a la base de datos principal o secundaria se redirige al nombre de red de instancia adecuado de la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o de la Instancia de clúster de conmutación por error (FCI) de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] subyacente.

 Las instancias de SQL Server se hospedan activamente en un solo nodo.
Si está presente, una Instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] independiente reside siempre en un único Nodo con un nombre de red de instancia estático.  Si está presente, una FCI de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] está activa en uno de dos o más nodos de conmutación por error posibles con un único Nombre de red de instancia virtual.

 Los nodos son miembros de un clúster de WSFC.
Los metadatos de configuración de WSFC y el estado de todos los nodos se almacenan en cada nodo. Cada servidor puede proporcionar volúmenes asimétricos de almacenamiento o almacenamiento compartido (SAN) para las bases de datos del sistema o de usuario. Cada servidor tiene al menos una interfaz de red física en una o varias subredes IP.

 El servicio WSFC supervisa el estado y administra la configuración de un grupo de servidores.
El servicio de Clúster de conmutación por error de Windows Server (WSFC) propaga los cambios en los metadatos y el estado de Configuración de WSFC a todos los nodos del clúster. Los metadatos y el estado parciales se pueden almacenar en un recurso compartido de archivos remoto de testigo de quórum de WSFC. Dos o más nodos o testigos activos constituyen un quórum para votar sobre el estado del clúster de WSFC.

 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] son subclaves del clúster de WSFC.
Si elimina y vuelve a crear un clúster de WSFC, debe deshabilitar y volver a habilitar la característica de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] en cada instancia del servidor habilitada para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] en el clúster de WSFC original. Para obtener más información, vea [Habilitar y deshabilitar grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).

 ![Diagrama de contexto de componentes de SQL Server AlwaysOn](../../../database-engine/media/alwaysoncomponentcontextdiagram.gif "Diagrama de contexto de componentes de SQL Server AlwaysOn")

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tareas relacionadas

-   [Ver la configuración de NodeWeight de cuórum de clúster](view-cluster-quorum-nodeweight-settings.md)

-   [Configurar los valores de NodeWeight de cuórum de clúster](configure-cluster-quorum-nodeweight-settings.md)

-   [Forzar el inicio de un clúster WSFC sin un quórum](force-a-wsfc-cluster-to-start-without-a-quorum.md)

##  <a name="related-content"></a><a name="RelatedContent"></a> Contenido relacionado

-   [Tecnologías de Windows Server: clústeres de conmutación por error](https://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx)

-   [Clústeres de conmutación por error de Windows Server 2008 R2](https://technet.microsoft.com/library/ff182338\(WS.10\).aspx)

-   [View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)

-   [Cmdlet de clúster de conmutación por error Get-ClusterLog](https://technet.microsoft.com/library/ee461045.aspx)

## <a name="see-also"></a>Consulte también
 Introducción a [las instancias de clúster de conmutación por error de AlwaysOn (SQL Server)](always-on-failover-cluster-instances-sql-server.md) [de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) [modos de cuórum de WSFC y configuración de votación](wsfc-quorum-modes-and-voting-configuration-sql-server.md) &#40;SQL Server [Directiva de conmutación por error para instancias de clúster de conmutación por error](failover-policy-for-failover-cluster-instances.md) [WSFC recuperación ante desastres mediante la&#41;de cuórum forzada](wsfc-disaster-recovery-through-forced-quorum-sql-server.md) &#40;


