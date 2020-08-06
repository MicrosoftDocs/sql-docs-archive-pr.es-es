---
title: Formas de minería de datos para Visio | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining shapes
- templates [Visio]
- Visio shapes
- shapes, data mining
ms.assetid: 11a821d9-1c0a-442e-b735-92208ce479dc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a12d7d5f3ad021105f06043f47dcdfe5c3e5c2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87675067"
---
# <a name="data-mining-shapes-for-visio"></a>Formas de minería de datos para Visio
  Las Formas de minería de datos para Visio proporcionan plantillas personalizadas para mostrar modelos de minería de datos. Mediante estas plantillas, puede conectarse a un modelo que ha creado y crear presentaciones interactivas para ilustrar los resultados de la minería de datos.  
  
 Las plantillas ofrecen muchas ventajas con respecto a las capturas de pantalla y los gráficos estáticos: interactúan con los modelos de minería de datos subyacentes, que se almacenan en una instancia de Analysis Services, y permiten personalizar la forma en que se muestran los patrones del modelo de minería de datos. Puede contraer y expandir un modelo de árbol, filtrar en los nodos de datos o por atributos, y mostrar las estadísticas del modelo como las probabilidades y los coeficientes.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Las plantillas de Visio incluyen estos asistentes:  
  
-   **Diagrama de red de dependencias:** Use este asistente para crear gráficos para árboles de decisión y redes neuronal.  
  
-   **Diagrama de árbol de decisión:** Use este asistente para crear diagramas que muestren los puntos de decisión y las fórmulas asociadas a los modelos de árbol de decisión. Este diagrama se puede utilizar también con modelos de regresión.  
  
-   **Diagrama del clúster:** Use este asistente para crear gráficos multicolor para los modelos de segmentación. Se puede alternar entre las vistas como distinción del atributo, perfiles del clúster y dependencias, y personalizar la apariencia de los clústeres.  
  
## <a name="installation"></a>Instalación  
 Al instalar las plantillas de minería de datos para Visio, los siguientes archivos se instalan de forma predeterminada en la carpeta \<drive> \Archivos de programa\microsoft SQL Server 2012 DM Add-Ins (o \<drive> en los archivos de programa (x86) \microsoft SQL Server 2012 DM-ins):  
  
-   **Minería de datos de Microsoft. VST** Esta plantilla contiene formato, diseño y asistentes prediseñados para ayudarle a trabajar con las formas de minería de datos.  
  
-   **Microsoft Data Mining Shape Studio. VSS** Este archivo de galería de símbolos contiene formas asociadas a la plantilla.  
  
## <a name="how-to-use-the-templates"></a>Cómo usar las plantillas  
 Para abrir las plantillas, puede hacer doble clic en el archivo de forma o puede abrir Visio y, a continuación, abrir la plantilla de formas.  
  
1.  Coloque una de las formas de minería de datos de Visio en una nueva página desde la galería de símbolos.  
  
2.  Cuando se inicie el asistente, conéctese al servidor que contiene el modelo de minería de datos que desea presentar.  
  
3.  Seleccione el modelo de minería de datos, de manera que el tipo de modelo coincida con el tipo de visualización.  
  
4.  Establezca las opciones que determinan cómo deben mostrarse los datos y el formato que deben tener.  
  
5.  Después de haber completado el **Asistente para crear formas de minería de datos**, tiene un diagrama que puede modificar y mejorar mediante las características de Visio.  
  
 Para obtener más información sobre cómo trabajar con diagramas de modelos de Visio y cómo mejorarlos, vea [ver modelos de minería de datos en visio &#40;complementos de minería de datos&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)  
  
## <a name="requirements"></a>Requisitos  
  
-   Para usar las plantillas, primero debe crear una conexión a una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
     El asistente le pedirá que seleccione un servidor de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] y que especifique la base de datos que contiene el modelo de minería de datos.  
  
     Para obtener información sobre cómo crear una conexión, vea [conectarse a los datos de origen &#40;cliente de minería de datos para Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
-   Si utiliza las Herramientas de análisis de tablas, asegúrese de guardar los modelos en el servidor de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] y no utilice modelos temporales.  
  
-   El modelo se debe haber creado con uno de los algoritmos admitidos: agrupación en clústeres, árboles de decisión, redes neuronal, Bayes Naive o regresión logística.  
  
  
