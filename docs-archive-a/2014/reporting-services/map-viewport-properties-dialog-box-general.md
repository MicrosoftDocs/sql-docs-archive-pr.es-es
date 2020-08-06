---
title: Cuadro de diálogo Propiedades de ventanilla de mapa, general | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d760d6a0572cbbd1bd948eab382c0727eb276c4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662648"
---
# <a name="map-viewport-properties-dialog-box-general"></a>Cuadro de diálogo Propiedades de ventanilla de mapa, General
  Seleccione **General** en el cuadro de diálogo **Propiedades de ventanilla de mapa** para cambiar las opciones del sistema de coordenadas, la proyección y los límites.  
  
## <a name="options"></a>Opciones  
 **Sistema de coordenadas**  
 Indique el tipo de sistema de coordenadas que el mapa de datos usa.  
  
-   **Planar** : elija esta opción cuando los datos del mapa estén en coordenadas X e Y, por ejemplo para generar planes.  
  
-   **Geográfico** : elija esta opción cuando los datos del mapa estén en coordenadas de longitud y latitud, por ejemplo para las ubicaciones de ciudades.  
  
 **Proyección**  
 Especifique el método que utilizar para proyectar las coordenadas geográficas en una superficie bidimensional. Elija una proyección que sea compatible con los datos que está visualizando. Las cuatro propiedades espaciales a las que afecta la proyección son el área, forma, distancia y dirección. Para las vistas de la tierra, una buena opción de proyección depende de la vista del centro, los límites del mapa y el factor de zoom.  
  
 Cada una de las proyecciones siguientes conserva una o varias de estas propiedades espaciales:  
  
-   **Equirectangular** : elija esta opción para utilizar la longitud y la latitud como coordenadas rectangulares.  
  
-   **Mercator** : elija esta proyección popular para las áreas más pequeñas, con menos distorsión alrededor del ecuador o cuando desee agregar una capa de mapa con una capa de mosaico existente que use la proyección Mercator.  
  
-   **Robinson** : elija esta opción para tener menos distorsión de áreas grandes que abarcan desde el ecuador a los polos. Fue desarrollado por Arthur H. Robinson en 1963.  
  
-   **Fahey** : elija esta opción para tener menos distorsión de las áreas grandes que abarcan desde el ecuador a los polos. Fue desarrollado por Lawrence Fahey en 1975.  
  
-   **Eckert1** : elija esta opción para utilizar paralelos igualmente espaciados en latitud y con líneas rectas para los meridianos en la longitud.  
  
-   **Eckert3** : elija esta opción para utilizar paralelos igualmente espaciados en latitud y con líneas curvas para los meridianos en la longitud.  
  
-   **HammerAitoff** : elija esta opción para los mapas polares o los mapas mundiales.  
  
-   **Wagner3** : elija esta opción para los mapas mundiales.  
  
-   **Bonne** : elija esta opción para ver el mundo tal como él aparece en un atlas.  
  
 **Opciones de salto de página**  
 Seleccione opciones para indicar la manera en que se ajusta el contenido a una página del informe.  
  
 **Opciones de límite**  
 Especifique los límites inferior y superior de las coordenadas para controlar qué parte del mapa aparece en el informe.  
  
 **X mínimo**  
 El valor de X inferior. Solo está disponible para **Planar** .  
  
 **X máximo**  
 El valor de X superior. Solo está disponible para **Planar** .  
  
 **Y mínimo**  
 El valor de Y inferior. Solo está disponible para **Planar** .  
  
 **Y máximo**  
 El valor de Y superior. Solo está disponible para **Planar** .  
  
 **Longitud mínima**  
 El valor de longitud inferior. Solo está disponible para **Geographic** .  
  
 **Longitud máxima**  
 El valor de longitud superior. Solo está disponible para **Geographic** .  
  
 **Latitud mínima**  
 El valor de latitud inferior. Solo está disponible para **Geographic** .  
  
 **Latitud máxima**  
 El valor de latitud superior. Solo está disponible para **Geographic** .  
  
## <a name="see-also"></a>Consulte también  
 [Mapas &#40;Generador de informes y SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)  
  
  
