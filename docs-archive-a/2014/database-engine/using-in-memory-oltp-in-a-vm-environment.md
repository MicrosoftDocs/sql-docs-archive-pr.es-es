---
title: Uso de OLTP en memoria en un entorno de máquina virtual | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83cf785fbcd2df9449d61e328e3bf8e374a6656d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87745961"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a>Uso de OLTP en memoria en un entorno de máquina virtual
  La virtualización del servidor puede ayudar a reducir la inversión y los costos operativos de TI y aumentar la eficacia de TI con mejores procesos de aprovisionamiento, mantenimiento, disponibilidad, copia de seguridad y recuperación. Con los avances tecnológicos recientes, es más fácil consolidar cargas de trabajo de base de datos complejas gracias a la virtualización. En este tema se tratan los procedimientos recomendados para el uso de [!INCLUDE[hek_1](../includes/hek-1-md.md)] en un entorno virtualizado.  
  
##  <a name="memory-pre-allocation"></a><a name="bkmk_memoryPreAllocation"></a>Asignación previa de memoria  
 Respecto a la memoria en un entorno virtualizado, son aspectos esenciales un mejor rendimiento y mayor compatibilidad. Debe ser capaz de asignar memoria rápidamente a las máquinas virtuales en función de sus requisitos (cargas pico y fuera de horas pico) y asegurarse de que la memoria no se desperdicia. La característica de memoria dinámica de Hyper-V aumenta la agilidad de cómo se asigna y administra la memoria entre las máquinas virtuales que se ejecutan en un host.  
  
 Es necesario modificar algunas prácticas recomendadas para virtualizar y administrar [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cuando se virtualiza una base de datos con tablas optimizadas para memoria. Sin tablas optimizadas para memoria, dos de los procedimientos recomendados son:  
  
-   Si se utiliza MIN_SERVER_MEMORY, es mejor asignar únicamente la cantidad de memoria que se necesita para que haya memoria suficiente para otros procesos (evitando de esta forma la paginación).  
  
-   No establecer un valor demasiado alto de asignación previa de memoria. De lo contrario, puede que otros procesos no obtengan memoria suficiente cuando la necesiten, y esto puede producir paginación de memoria.  
  
 Si sigue los procedimientos anteriores para una base de datos con tablas optimizadas para memoria, el intento de restaurar y recuperar una base de datos podría dar lugar a que esta pasara a un estado "Pendiente de recuperación", incluso si hay memoria suficiente para recuperarla. El motivo es que, al iniciarse, [!INCLUDE[hek_2](../includes/hek-2-md.md)] pone los datos en memoria de forma mucho más dinámica que la forma en que la asignación de memoria dinámica asigna la memoria necesaria a la base de datos.  
  
 **Resolución**  
  
 Para mitigar este problema, asigne previamente memoria suficiente a la base de datos para recuperar o reiniciar la base de datos; no especifique un valor mínimo confiando en que la memoria dinámica proporcionará memoria adicional cuando sea necesario.  
  
## <a name="see-also"></a>Consulte también  
 [OLTP en memoria &#40;optimización en memoria&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
