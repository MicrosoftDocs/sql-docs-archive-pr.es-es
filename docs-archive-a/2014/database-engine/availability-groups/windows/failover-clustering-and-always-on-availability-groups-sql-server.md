---
title: Clústeres de conmutación por error y Grupos de disponibilidad AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- clustering [SQL Server]
- Availability Groups [SQL Server], WSFC clusters
- Failover Cluster Instances [SQL Server], see failover clustering [SQL Server]
- quorum [SQL Server]
- failover clustering [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], Failover Cluster Instances
ms.assetid: 613bfbf1-9958-477b-a6be-c6d4f18785c3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64ee815c2b852849d9506ca6c3fc114d3d0e4935
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87672272"
---
# <a name="failover-clustering-and-alwayson-availability-groups-sql-server"></a>Clúster de conmutación por error y grupos de disponibilidad de AlwaysOn (SQL Server)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], la solución de alta disponibilidad y recuperación ante desastres introducida en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], requiere clústeres de conmutación por error de Windows Server (WSFC). Además, aunque [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] no depende de los clústeres de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , se puede utilizar una instancia de clústeres de conmutación por error (FCI) para hospedar una réplica de disponibilidad para un grupo de disponibilidad. Es importante conocer el rol de cada tecnología de clústeres y saber qué consideraciones son necesarias cuando se diseña el entorno de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .  
  
> [!NOTE]  
>  Para obtener información sobre los conceptos de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vea [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  

  
##  <a name="windows-server-failover-clustering-and-availability-groups"></a><a name="WSFC"></a>Clústeres de conmutación por error de Windows Server y grupos de disponibilidad  
 La implementación de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] requiere un clúster de WSFC (clústeres de conmutación por error de Windows Server). Para que una instancia de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]se habilite para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , debe residir en un nodo de WSFC y el clúster y el nodo de WSFC deben estar en línea. Además, cada réplica de disponibilidad de un determinado grupo de disponibilidad debe residir en otro nodo del mismo clúster de WSFC. La única excepción es que mientras se migra a otro clúster de WSFC, un grupo de disponibilidad puede ocupar temporalmente dos clústeres.  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] se basa en el clúster de clústeres de conmutación por error de Windows (WSFC) para supervisar y administrar los roles actuales de las réplicas de disponibilidad que pertenecen a un grupo de disponibilidad concreto, así como para determinar cómo afecta un evento de conmutación por error a las réplicas de disponibilidad. Por cada grupo de disponibilidad que cree, se creará un grupo de recursos de WSFC. El clúster de WSFC supervisa este grupo de recursos para evaluar el estado de la réplica principal.  
  
 El quorum para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] se basa en todos los nodos del clúster de WSFC independientemente de si un nodo de clúster determinado hospeda alguna réplica de disponibilidad. A diferencia de la creación de reflejo de la base de datos, no hay ningún rol testigo en [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
 Los votos de quórum de nodos del clúster determinan el estado general de un clúster de WSFC. Si el clúster de WSFC se queda sin conexión debido a un desastre no planeado, o a un error persistente de hardware o de comunicaciones, se necesita la intervención manual del administrador. Un administrador de clústeres de Windows Server o de WSFC necesitará forzar un quórum y volver a poner en línea los nodos del clúster superviviente en una configuración sin tolerancia a errores.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] son subclaves del clúster de WSFC. Si elimina y vuelve a crear un clúster de WSFC, debe deshabilitar y volver a habilitar la característica de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] en cada instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que hospedaba una réplica de disponibilidad en el clúster de WSFC original.  
  
 Para obtener información sobre cómo ejecutar [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en nodos de clústeres de conmutación por error de Windows Server (WSFC) y sobre el cuórum de WSFC, vea [Clústeres de conmutación por error de Windows Server &#40;WSFC&#41; con SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md).  
  
### <a name="cross-cluster-migration-of-alwayson-availability-groups-for-os-upgrade"></a>Migración entre clústeres de grupos de disponibilidad AlwaysOn para la actualización del sistema operativo  
 A partir de [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] admite la migración entre clústeres de grupos de disponibilidad para las implementaciones en un nuevo clúster de Clústeres de conmutación por error de Windows Server (WSFC). Una migración entre clústeres mueve un grupo de disponibilidad o un lote de grupos de disponibilidad al nuevo clúster de WSFC de destino con un tiempo de inactividad mínimo. El proceso de migración entre clústeres le permite mantener los contratos de nivel de servicio (SLA) al actualizar a un clúster de [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] . [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] (o una versión posterior) debe estar instalado y habilitado para AlwaysOn en el clúster de WSFC de destino. El éxito de una migración entre clústeres depende de un planeamiento y una preparación exhaustivos del clúster de WSFC de destino.  
  
 Para obtener más información, vea [Migración entre clústeres de grupos de disponibilidad AlwaysOn para la actualización del sistema operativo](https://msdn.microsoft.com/library/jj873730.aspx).  
  
##  <a name="ssnoversion-failover-cluster-instances-fcis-and-availability-groups"></a><a name="SQLServerFC"></a> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instancias de clúster de conmutación por error (FCI) y grupos de disponibilidad  
 Puede configurar un segundo nivel de conmutación por error en el nivel de instancia de servidor si implementa los clústeres de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] junto con el clúster de WSFC. Una réplica de disponibilidad se puede hospedar en una instancia independiente de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o una instancia de FCI. Solo un asociado de FCI puede hospedar una réplica para un grupo de disponibilidad dado. Cuando una réplica de disponibilidad se ejecuta en una instancia de clúster de conmutación por error (FCI), la lista de posibles propietarios del grupo de disponibilidad contendrá solo el nodo de FCI activo.  
  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] no depende de ninguna forma de almacenamiento compartido. Sin embargo, si usa una instancia de clúster de conmutación por error (FCI) de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para hospedar una o varias réplicas de disponibilidad, cada una de las FCI requerirá almacenamiento compartido según la instalación típica de la instancia de clúster de conmutación por error de SQL Server.  
  
 Para más información sobre los requisitos previos adicionales, vea la sección "Requisitos previos y restricciones para usar una instancia de clúster de conmutación por error (FCI) de SQL Server para hospedar una réplica de disponibilidad" de [Requisitos previos, restricciones y recomendaciones para grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
### <a name="comparison-of-failover-cluster-instances-and-availability-groups"></a>Comparación de las instancias de clúster de conmutación por error y los grupos de disponibilidad  
 Independientemente del número de nodos de la FCI, una FCI completa hospeda una sola réplica en un grupo de disponibilidad. En la tabla siguiente se describen las diferencias conceptuales entre los nodos en una FCI y las réplicas en un grupo de disponibilidad.  
  
||Nodos en una FCI|Réplicas en un grupo de disponibilidad|  
|-|-------------------------|-------------------------------------------|  
|**Usa el clúster de WSFC**|Sí|Sí|  
|**Nivel de protección**|Instancia|Base de datos|  
|**Tipo de almacenamiento**|Compartido|No compartidos<br /><br /> Tenga en cuenta que mientras las réplicas de un grupo de disponibilidad no comparten almacenamiento, una réplica hospedada por una FCI usa una solución de almacenamiento compartido de acuerdo con esa FCI. La solución de almacenamiento es compartida solo por los nodos en la FCI y no entre las réplicas del grupo de disponibilidad.|  
|**Soluciones de almacenamiento**|Se adjuntan directamente, SAN, puntos de montaje, SMB|Depende del tipo de nodo|  
|**Secundarios legibles**|No*|Sí|  
|**Opciones aplicables de la directiva de conmutación por error**|Quórum de WSFC<br /><br /> Específico de FCI<br /><br /> Configuración de grupo de disponibilidad**|Quórum de WSFC<br /><br /> Configuración de grupos de disponibilidad|  
|**Recursos conmutados por error**|Servidor, instancia y base de datos|Solo base de datos|  
  
 *Mientras que las réplicas secundarias sincrónicas de un grupo de disponibilidad se ejecutan siempre en las instancias respectivas de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , los nodos secundarios de una FCI no han iniciado realmente las instancias respectivas de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y, por lo tanto, no son legibles. En una FCI, un nodo secundario inicia la instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cuando la propiedad del grupo de recursos se le transfiere durante una conmutación por error de FCI. Sin embargo, en el nodo de FCI activo, cuando una base de datos hospedada por FCI pertenece a un grupo de disponibilidad, si la réplica de disponibilidad local se ejecuta como réplica secundaria legible, la base de datos es legible.  
  
 **La configuración de la directiva de conmutación por error del grupo de disponibilidad se aplica a todas las réplicas, ya estén hospedadas en una instancia independiente o una instancia de FCI.  
  
> [!NOTE]  
>  Para obtener más información acerca del **número de nodos** en los clústeres de conmutación por error y **grupos de disponibilidad AlwaysOn** para diferentes ediciones de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , vea [características compatibles con las ediciones de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) ( https://go.microsoft.com/fwlink/?linkid=232473) .  
  
### <a name="considerations-for-hosting-an-availability-replica-on-an-fci"></a>Consideraciones para hospedar una réplica de disponibilidad en una FCI  
  
> [!IMPORTANT]  
>  Si tiene previsto hospedar una réplica de disponibilidad en una instancia de clúster de conmutación por error (FCI) de SQL Server, asegúrese de que los nodos de host de Windows Server 2008 cumplen con los requisitos previos y las restricciones de AlwaysOn para las instancias de clúster de conmutación por error (FCI). Para más información, vea [Requisitos previos, restricciones y recomendaciones para grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Las instancias de clúster de conmutación por error (FCI) no admiten la conmutación automática por error de grupos de disponibilidad; por lo tanto, todas las réplicas de disponibilidad hospedadas por un FCI solo se pueden configurar para la conmutación por error manual.  
  
 Es posible que necesite configurar un clúster de conmutación por error de Windows Server (WSFC) para incluir los discos compartidos que no están disponibles en todos los nodos. Por ejemplo, considere un clúster de WSFC en dos centros de datos con tres nodos. Dos de los nodos hospedan una instancia de clúster de conmutación por error (FCI) de SQL Server en el centro de datos principal y tienen acceso a los mismos discos compartidos. El tercer nodo hospeda una instancia independiente de SQL Server en otro centro de datos y no tiene acceso a los discos compartidos desde el centro de datos principal. Esta configuración de clúster de WSFC admite la implementación de un grupo de disponibilidad si la FCI hospeda la réplica principal y la instancia independiente hospeda la réplica secundaria.  
  
 Al elegir una FCI para hospedar una réplica de disponibilidad para un grupo de disponibilidad determinado, asegúrese de que una conmutación por error de FCI no puede hacer que un único nodo de WSFC intente hospedar dos réplicas de disponibilidad para el mismo grupo de disponibilidad.  
  
 El escenario de ejemplo siguiente muestra cómo podría producir problemas esta configuración:  
  
 Marcel configura un clúster de WSFC con dos nodos, `NODE01` y `NODE02`. Instala una instancia de clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , `fciInstance1`, en `NODE01` y `NODE02` , donde `NODE01` es el propietario actual de `fciInstance1`.  
 En `NODE02`, Marcel instala otra instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], `Instance3`, que es una instancia independiente.  
 En `NODE01`, Marcel habilita fciInstance1 para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. En `NODE02`, habilita `Instance3` para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. A continuación, configura un grupo de disponibilidad para el que `fciInstance1` hospeda la réplica principal e `Instance3` hospeda la réplica secundaria.  
 En algún momento `fciInstance1` deja de estar disponible en `NODE01`y el clúster de WSFC produce una conmutación por error de `fciInstance1` a `NODE02`. Después de la conmutación por error, `fciInstance1` es una instancia habilitada para [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]que se ejecuta en el rol principal de `NODE02`. Sin embargo, `Instance3` reside ahora en el mismo nodo de WSFC que `fciInstance1`. Esto infringe la restricción de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .  
 Para corregir el problema que este escenario produce, la instancia independiente, `Instance3`, debe residir en otro nodo del mismo clúster de WSFC que `NODE01` y `NODE02`.  
  
 Para más información sobre los clústeres de conmutación por error de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vea [Instancias de clúster de conmutación por error de AlwaysOn &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
##  <a name="restrictions-on-using-the-wsfc-failover-cluster-manager-with-availability-groups"></a><a name="FCMrestrictions"></a>Restricciones en el uso del Administrador de clústeres de conmutación por error WSFC con grupos de disponibilidad  
 No use el Administrador de clústeres de conmutación por error para manipular grupos de disponibilidad, por ejemplo:  
  
-   No agregue ni quite recursos en el servicio en clúster (grupo de recursos) para el grupo de disponibilidad.  
  
-   No cambie las propiedades de los grupos de disponibilidad, como los propietarios posibles y los propietarios preferidos. El grupo de disponibilidad establece automáticamente estas propiedades.  
  
-   No use el Administrador de clústeres de conmutación por error para mover los grupos de disponibilidad a otros nodos o para conmutar los grupos de disponibilidad. El Administrador de clústeres de conmutación por error no conoce el estado de sincronización de las réplicas de disponibilidad y hacer esto puede conducir a un tiempo de inactividad extendido. Debe usar [!INCLUDE[tsql](../../../includes/tsql-md.md)] o [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenido relacionado  
  
-   **Blogs:**  
  
     [Configurar el clúster de conmutación por error de Windows para SQL Server (grupo de disponibilidad o FCI) con seguridad limitada](https://blogs.msdn.com/b/sqlalwayson/archive/2012/06/05/configure-windows-failover-clustering-for-sql-server-availability-group-or-fci-with-limited-security.aspx)  
  
     [Blogs del equipo de AlwaysOn de SQL Server: el blog oficial del equipo de AlwaysOn de SQL Server](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs de los ingenieros de SQL Server de CSS](https://blogs.msdn.com/b/psssql/)  
  
-   **Notas del producto:**  
  
     [Guía de la arquitectura de AlwaysOn: generar una solución de alta disponibilidad y recuperación ante desastres mediante instancias de clúster de conmutación por error y grupos de disponibilidad](https://msdn.microsoft.com/library/jj215886.aspx)  
  
     [Guía de soluciones AlwaysOn de Microsoft SQL Server para lograr alta disponibilidad y recuperación ante desastres](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Notas del producto de Microsoft para SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Notas del producto del equipo de asesoramiento al cliente de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Consulte también  
 [Información general de Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) [habilitar y deshabilitar grupos de disponibilidad AlwaysOn](enable-and-disable-always-on-availability-groups-sql-server.md) &#40;SQL Server&#41;[supervisar grupos de disponibilidad &#40;Transact-SQL&#41;](monitor-availability-groups-transact-sql.md)  
 [Instancias de clúster de conmutación por error de AlwaysOn &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) 
  
  
