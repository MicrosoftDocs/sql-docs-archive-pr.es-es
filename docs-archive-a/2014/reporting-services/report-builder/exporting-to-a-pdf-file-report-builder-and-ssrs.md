---
title: Exportar a un archivo PDF (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f22497b7-f6c1-4c7b-b831-8c731e26ae37
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b4a324ad40d01d302196fe40ffb4232deb62a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87662625"
---
# <a name="exporting-to-a-pdf-file-report-builder-and-ssrs"></a><span data-ttu-id="289ae-102">Exportar a un archivo PDF (Generador de informes y SSRS)</span><span class="sxs-lookup"><span data-stu-id="289ae-102">Exporting to a PDF File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="289ae-103">La extensión de representación en PDF representa un informe en archivos que se pueden abrir en Adobe Acrobat y en visores de PDF de otros fabricantes que admiten PDF 1.3.</span><span class="sxs-lookup"><span data-stu-id="289ae-103">The PDF rendering extension renders a report to files that can be opened in Adobe Acrobat and other third-party PDF viewers that support PDF 1.3.</span></span> <span data-ttu-id="289ae-104">Aunque PDF 1.3 es compatible con Adobe Acrobat 4.0 y versiones posteriores, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] admite Adobe Acrobat 6 o posterior.</span><span class="sxs-lookup"><span data-stu-id="289ae-104">Although PDF 1.3 is compatible with Adobe Acrobat 4.0 and later versions, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supports Adobe Acrobat 6 or later.</span></span> <span data-ttu-id="289ae-105">La extensión de representación no requiere el software Adobe para representar el informe.</span><span class="sxs-lookup"><span data-stu-id="289ae-105">The rendering extension does not require Adobe software to render the report.</span></span> <span data-ttu-id="289ae-106">Sin embargo, se necesitan visores de PDF, como Adobe Acrobat, para ver o imprimir un informe en formato PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-106">However, PDF viewers such as Adobe Acrobat are required to view or print a report in PDF format.</span></span>  
  
 <span data-ttu-id="289ae-107">La extensión de representación en PDF admite caracteres ANSI y puede traducir caracteres Unicode del japonés, coreano, chino tradicional, chino simplificado, cirílico, hebreo y árabe, con ciertas limitaciones.</span><span class="sxs-lookup"><span data-stu-id="289ae-107">The PDF rendering extension supports ANSI characters and can translate Unicode characters from Japanese, Korean, Traditional Chinese, Simplified Chinese, Cyrillic, Hebrew, and Arabic with certain limitations.</span></span> <span data-ttu-id="289ae-108">Para obtener más información sobre las limitaciones, vea [exportar informes &#40;generador de informes y SSRS&#41;](export-reports-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="289ae-108">For more information about the limitations, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="289ae-109">El representador de PDF es un representador en página física y, por consiguiente, tiene un comportamiento de paginación que difiere del de otros representadores como HTML y Excel.</span><span class="sxs-lookup"><span data-stu-id="289ae-109">The PDF renderer is a physical page renderer and, therefore, has pagination behavior that differs from other renderers such as HTML and Excel.</span></span> <span data-ttu-id="289ae-110">En este tema se proporciona información específica del representador de PDF y se describen las excepciones a las reglas.</span><span class="sxs-lookup"><span data-stu-id="289ae-110">This topic provides PDF renderer-specific information and describes exceptions to the rules.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="font-embedding"></a><a name="FontRequirements"></a><span data-ttu-id="289ae-111">Incrustación de fuentes</span><span class="sxs-lookup"><span data-stu-id="289ae-111">Font Embedding</span></span>  
 <span data-ttu-id="289ae-112">Siempre que sea posible, la extensión de representación en PDF incrustará el subconjunto de cada una de las fuentes que sea necesaria para mostrar el informe en el archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-112">When possible, the PDF rendering extension embeds the subset of each font that is needed to display the report in the PDF file.</span></span> <span data-ttu-id="289ae-113">Las fuentes que se utilicen en el informe deberán instalarse en el servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="289ae-113">Fonts that are used in the report must be installed on the report server.</span></span> <span data-ttu-id="289ae-114">Cuando el servidor de informes genera un informe en formato PDF, usa la información almacenada en la fuente a la que hace referencia el informe para crear asignaciones de caracteres en el archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-114">When the report server generates a report in PDF format, it uses the information stored in the font referenced by the report to create character mappings within the PDF file.</span></span> <span data-ttu-id="289ae-115">Si la fuente a la que se hace referencia no está instalada en el servidor de informes, es posible que el archivo PDF resultante no contenga las asignaciones correctas y, por lo tanto, no se muestre correctamente cuando se visualice.</span><span class="sxs-lookup"><span data-stu-id="289ae-115">If the referenced font is not installed on the report server, the resulting PDF file might not contain the correct mappings and might not display correctly when viewed.</span></span>  
  
 <span data-ttu-id="289ae-116">Las fuentes se incrustan en el archivo PDF cuando se dan las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="289ae-116">Fonts are embedded in the PDF file when the following conditions apply:</span></span>  
  
-   <span data-ttu-id="289ae-117">El autor de la fuente concede privilegios de incrustación para la fuente.</span><span class="sxs-lookup"><span data-stu-id="289ae-117">Font embedding privileges are granted by the font author.</span></span> <span data-ttu-id="289ae-118">Las fuentes instaladas incluyen una propiedad que indica si el autor de la fuente tiene intención de permitir la incrustación de una fuente en un documento.</span><span class="sxs-lookup"><span data-stu-id="289ae-118">Installed fonts include a property that indicates whether the font author intends to allow embedding a font in a document.</span></span> <span data-ttu-id="289ae-119">Si el valor de la propiedad es EMBED_NOEMBEDDING, la fuente no se incrustará en el archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-119">If the property value is EMBED_NOEMBEDDING, the font is not embedded in the PDF file.</span></span> <span data-ttu-id="289ae-120">Para obtener más información, vea "TTGetEmbeddingType" en msdn.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="289ae-120">For more information, see "TTGetEmbeddingType" on msdn.microsoft.com.</span></span>  
  
-   <span data-ttu-id="289ae-121">La propiedad Font es TrueType.</span><span class="sxs-lookup"><span data-stu-id="289ae-121">The Font is TrueType.</span></span>  
  
-   <span data-ttu-id="289ae-122">Hacen referencia a las fuentes los elementos visibles de un informe.</span><span class="sxs-lookup"><span data-stu-id="289ae-122">Fonts are referenced by visible items in a report.</span></span> <span data-ttu-id="289ae-123">Si se hace referencia a una fuente mediante un elemento que tiene la propiedad Hidden establecida en True, no es necesario que la fuente muestre los datos representados y no se incluirá en el archivo.</span><span class="sxs-lookup"><span data-stu-id="289ae-123">If a font is referenced by an item that has the Hidden property set to True, the font is not needed to display rendered data and will not be included in the file.</span></span> <span data-ttu-id="289ae-124">Las fuentes solamente se incrustan cuando tienen que mostrar los datos de informe representados.</span><span class="sxs-lookup"><span data-stu-id="289ae-124">Fonts are embedded only when they are needed to display the rendered report data.</span></span>  
  
 <span data-ttu-id="289ae-125">Si se cumplen todas estas condiciones para una fuente, la fuente se incrusta en el archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-125">If all of these conditions are met for a font, the font is embedded in the PDF file.</span></span> <span data-ttu-id="289ae-126">Si no se cumple alguna de estas condiciones, o varias, la fuente no se incrusta en el archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-126">If one or more of these conditions is not met, the font is not embedded in the PDF file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="289ae-127">Aunque se cumplan las condiciones, hay una circunstancia en la que no se incrustan fuentes en el archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-127">Although the conditions are met, there is one circumstance under which fonts are not embedded in the PDF file.</span></span> <span data-ttu-id="289ae-128">Si las fuentes usadas son las de la especificación de PDF que se conoce normalmente como fuentes estándar de tipo 1 o fuentes de base catorce, no se incrustan fuentes para el contenido ANSI.</span><span class="sxs-lookup"><span data-stu-id="289ae-128">If the fonts used are the ones in the PDF specification that are commonly known as standard type 1 fonts or the base fourteen fonts, then fonts are not embedded for ANSI content.</span></span>  
  
  
  
### <a name="fonts-on-the-client-computer"></a><span data-ttu-id="289ae-129">Fuentes en el equipo cliente</span><span class="sxs-lookup"><span data-stu-id="289ae-129">Fonts on the Client Computer</span></span>  
 <span data-ttu-id="289ae-130">Cuando una fuente se incrusta en el archivo PDF, el equipo que se usa para ver el informe (equipo cliente) no necesita tener la fuente instalada para que el informe se muestre correctamente.</span><span class="sxs-lookup"><span data-stu-id="289ae-130">When a font is embedded in the PDF file, the computer that is used to view the report (the client computer) does not need to have the font installed for the report to display correctly.</span></span>  
  
 <span data-ttu-id="289ae-131">Cuando una fuente no se incrusta en el archivo PDF, el equipo cliente debe tener instalada la fuente correcta para que el informe se muestre correctamente.</span><span class="sxs-lookup"><span data-stu-id="289ae-131">When a font is not embedded in the PDF file, the client computer must have the correct font installed for the report to display correctly.</span></span> <span data-ttu-id="289ae-132">Si la fuente no está instalada en el equipo cliente, el archivo PDF muestra un carácter de signo de interrogación de cierre (?) para los caracteres no compatibles.</span><span class="sxs-lookup"><span data-stu-id="289ae-132">If the font is not installed on the client computer, the PDF file displays a question mark character (?) for unsupported characters.</span></span>  
  
### <a name="verifying-fonts-in-a-pdf-file"></a><span data-ttu-id="289ae-133">Comprobar las fuentes de un archivo PDF</span><span class="sxs-lookup"><span data-stu-id="289ae-133">Verifying Fonts in a PDF File</span></span>  
 <span data-ttu-id="289ae-134">Suelen producirse diferencias en la salida en PDF si se usa una fuente que no admite caracteres no latinos en un informe y, a continuación, se agregan caracteres no latinos al informe.</span><span class="sxs-lookup"><span data-stu-id="289ae-134">Differences in PDF output occur most often when a font that does not support non-Latin characters is used in a report and then non-Latin characters are added to the report.</span></span> <span data-ttu-id="289ae-135">Se debe comprobar la salida de representación en PDF tanto en el servidor de informes como en los equipos cliente para comprobar que el informe se representa correctamente.</span><span class="sxs-lookup"><span data-stu-id="289ae-135">You should test the PDF rendering output on both the report server and the client computers to verify that the report renders correctly.</span></span>  
  
 <span data-ttu-id="289ae-136">No confíe en la visualización del informe en vista previa ni en la exportación a HTML, ya que el informe parece correcto por la sustitución de fuentes automática realizada por la interfaz de diseño gráfico o por Microsoft Internet Explorer, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="289ae-136">Do not rely on viewing the report in Preview or exporting to HTML because the report will look correct due to automatic font substitution performed by the graphical design interface or by Microsoft Internet Explorer, respectively.</span></span> <span data-ttu-id="289ae-137">Si faltan glifos de Unicode en el servidor, es posible que vea caracteres reemplazados por un signo de interrogación de cierre (?).</span><span class="sxs-lookup"><span data-stu-id="289ae-137">If there are Unicode Glyphs missing on the server, you may see characters replaced with a question mark (?).</span></span> <span data-ttu-id="289ae-138">Si falta una fuente en el cliente, puede ver que algunos caracteres se reemplazan con cuadros (□).</span><span class="sxs-lookup"><span data-stu-id="289ae-138">If there is a font missing on the client, you may see characters replaced with boxes (□).</span></span>  
  
 <span data-ttu-id="289ae-139">Las fuentes incrustadas en el archivo PDF se incluyen en la propiedad Fonts que se guarda con el archivo, en forma de metadatos.</span><span class="sxs-lookup"><span data-stu-id="289ae-139">The fonts that are embedded in the PDF file are included in the Fonts property that is saved with the file, as metadata.</span></span>  
  
##  <a name="metadata"></a><a name="Metadata"></a> <span data-ttu-id="289ae-140">Metadatos</span><span class="sxs-lookup"><span data-stu-id="289ae-140">Metadata</span></span>  
 <span data-ttu-id="289ae-141">Además del diseño del informe, la extensión de representación en PDF escribe los metadatos siguientes en el diccionario de información del documento PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-141">In addition to the report layout, the PDF rendering extension writes the following metadata to the PDF Document Information Dictionary.</span></span>  
  
|<span data-ttu-id="289ae-142">Propiedad de PDF</span><span class="sxs-lookup"><span data-stu-id="289ae-142">PDF property</span></span>|<span data-ttu-id="289ae-143">Creada a partir de</span><span class="sxs-lookup"><span data-stu-id="289ae-143">Created from</span></span>|  
|------------------|------------------|  
|`Title`|<span data-ttu-id="289ae-144">El atributo `Name` del elemento RDL `Report`.</span><span class="sxs-lookup"><span data-stu-id="289ae-144">The `Name` attribute of the `Report` RDL element.</span></span>|  
|`Author`|<span data-ttu-id="289ae-145">El elemento RDL `Author`.</span><span class="sxs-lookup"><span data-stu-id="289ae-145">The `Author` RDL element.</span></span>|  
|`Subject`|<span data-ttu-id="289ae-146">El elemento RDL `Description`.</span><span class="sxs-lookup"><span data-stu-id="289ae-146">The `Description` RDL element.</span></span>|  
|`Creator`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="289ae-147">.</span><span class="sxs-lookup"><span data-stu-id="289ae-147">product name and version.</span></span>|  
|`Producer`|<span data-ttu-id="289ae-148">El nombre y la versión de la extensión de representación.</span><span class="sxs-lookup"><span data-stu-id="289ae-148">Rendering extension name and version.</span></span>|  
|`CreationDate`|<span data-ttu-id="289ae-149">La hora de ejecución del informe en el formato `datetime` de PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-149">Report execution time in PDF `datetime` format.</span></span>|  
  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="289ae-150">Interactividad</span><span class="sxs-lookup"><span data-stu-id="289ae-150">Interactivity</span></span>  
 <span data-ttu-id="289ae-151">Algunos elementos interactivos se admiten en PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-151">Some interactive elements are supported in PDF.</span></span> <span data-ttu-id="289ae-152">A continuación se describen sus comportamientos específicos.</span><span class="sxs-lookup"><span data-stu-id="289ae-152">The following is a description of specific behaviors.</span></span>  
  
### <a name="show-and-hide"></a><span data-ttu-id="289ae-153">Mostrar u ocultar</span><span class="sxs-lookup"><span data-stu-id="289ae-153">Show and Hide</span></span>  
 <span data-ttu-id="289ae-154">El formato PDF no permite mostrar y ocultar elementos dinámicamente.</span><span class="sxs-lookup"><span data-stu-id="289ae-154">Dynamic show and hide elements are not supported in PDF.</span></span> <span data-ttu-id="289ae-155">El documento PDF se representa para que coincida con el estado actual de cualquier elemento del informe.</span><span class="sxs-lookup"><span data-stu-id="289ae-155">The PDF document is rendered to match the current state of any items in the report.</span></span> <span data-ttu-id="289ae-156">Por ejemplo, si el elemento se mostraba cuando se ejecutó inicialmente el informe, el elemento se representará.</span><span class="sxs-lookup"><span data-stu-id="289ae-156">For example, if the item is displayed when the report is run initially, then the item is rendered.</span></span> <span data-ttu-id="289ae-157">Las imágenes que pueden alternarse no se representarán si estaban ocultas al exportar el informe.</span><span class="sxs-lookup"><span data-stu-id="289ae-157">Images that can be toggled are not rendered, if they are hidden when the report is exported.</span></span>  
  
### <a name="document-map"></a><span data-ttu-id="289ae-158">Mapa del documento</span><span class="sxs-lookup"><span data-stu-id="289ae-158">Document Map</span></span>  
 <span data-ttu-id="289ae-159">Si hay alguna etiqueta de mapa del documento presente en el informe, se agrega un esquema de documento al archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-159">If there are any document map labels present in the report, a document outline is added to the PDF file.</span></span> <span data-ttu-id="289ae-160">Cada etiqueta de mapa del documento aparece como una entrada en el esquema de documento en el orden en el que figura en el informe.</span><span class="sxs-lookup"><span data-stu-id="289ae-160">Each document map label appears as an entry in the document outline in the order that it appears in the report.</span></span> <span data-ttu-id="289ae-161">En Acrobat, solo se agrega un marcador de destino al esquema del documento si se representa la página en la que aparece.</span><span class="sxs-lookup"><span data-stu-id="289ae-161">In Acrobat, a target bookmark is added to the document outline only if the page it is on is rendered.</span></span>  
  
 <span data-ttu-id="289ae-162">Si solo se representa una página, no se agrega ningún esquema de documento.</span><span class="sxs-lookup"><span data-stu-id="289ae-162">If only a single page is rendered, no document outline is added.</span></span> <span data-ttu-id="289ae-163">El mapa del documento se organiza jerárquicamente para reflejar el nivel de anidamiento del informe.</span><span class="sxs-lookup"><span data-stu-id="289ae-163">The document map is arranged hierarchically to reflect the level of nesting in the report.</span></span> <span data-ttu-id="289ae-164">El esquema del documento es accesible en Acrobat en la pestaña marcadores. al hacer clic en una entrada dentro del esquema del documento, el documento se desplaza a la ubicación marcada.</span><span class="sxs-lookup"><span data-stu-id="289ae-164">The document outline is accessible in Acrobat under the Bookmarks tab. Clicking an entry within the document outline causes the document to go to the bookmarked location.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="289ae-165">Marcadores</span><span class="sxs-lookup"><span data-stu-id="289ae-165">Bookmarks</span></span>  
 <span data-ttu-id="289ae-166">No se admiten marcadores en la representación en PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-166">Bookmarks are not supported in PDF rendering.</span></span>  
  
### <a name="drillthrough-links"></a><span data-ttu-id="289ae-167">Vínculos de obtención de detalles</span><span class="sxs-lookup"><span data-stu-id="289ae-167">Drillthrough Links</span></span>  
 <span data-ttu-id="289ae-168">Los vínculos de obtención de detalles no se admiten en representación de PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-168">Drillthrough links are not supported in PDF rendering.</span></span> <span data-ttu-id="289ae-169">Los vínculos de obtención de detalles no se representan como vínculos en los que se puede hacer clic y los informes detallados no se pueden conectar con el destino de la obtención de detalles.</span><span class="sxs-lookup"><span data-stu-id="289ae-169">The drillthrough links are not rendered as clickable links and drillthrough reports cannot connect to the target of the drillthrough.</span></span>  
  
### <a name="hyperlinks"></a><span data-ttu-id="289ae-170">Hipervínculos</span><span class="sxs-lookup"><span data-stu-id="289ae-170">Hyperlinks</span></span>  
 <span data-ttu-id="289ae-171">Los hipervínculos de los informes se representan como vínculos en los que puede hacerse clic en el archivo PDF.</span><span class="sxs-lookup"><span data-stu-id="289ae-171">Hyperlinks in reports are rendered as clickable links in the PDF file.</span></span> <span data-ttu-id="289ae-172">Al hacer clic en ellos, Acrobat abrirá el explorador predeterminado del cliente y navegará a la dirección URL del hipervínculo.</span><span class="sxs-lookup"><span data-stu-id="289ae-172">When clicked, Acrobat will open the default client browser and navigate to the hyperlink URL.</span></span>  
  
  
  
##  <a name="compression"></a><a name="Compression"></a><span data-ttu-id="289ae-173">Presi</span><span class="sxs-lookup"><span data-stu-id="289ae-173">Compression</span></span>  
 <span data-ttu-id="289ae-174">La compresión de imágenes está basada en el tipo de archivo original de la imagen.</span><span class="sxs-lookup"><span data-stu-id="289ae-174">Image compression is based on the original file type of the image.</span></span> <span data-ttu-id="289ae-175">La extensión de representación en PDF comprime los archivos PDF de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="289ae-175">The PDF rendering extension compresses PDF files by default.</span></span>  
  
 <span data-ttu-id="289ae-176">Para conservar la compresión de las imágenes incluidas en el archivo PDF siempre que sea posible, las imágenes JPEG se almacenan como JPEG y el resto de tipos de imagen se almacenan como BMP.</span><span class="sxs-lookup"><span data-stu-id="289ae-176">To preserve any compression for images included in the PDF file when possible, JPEG images are stored as JPEG and all other image types are stored as BMP.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="289ae-177">Los archivos PDF no admiten la inserción de imágenes PNG.</span><span class="sxs-lookup"><span data-stu-id="289ae-177">PDF files don't support embedding PNG images.</span></span>  
  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="289ae-178">Configuración de la información del dispositivo</span><span class="sxs-lookup"><span data-stu-id="289ae-178">Device Information Settings</span></span>  
 <span data-ttu-id="289ae-179">Puede cambiar parte de la configuración predeterminada de este representador cambiando los valores de configuración de la información del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="289ae-179">You can change some default settings for this renderer by changing the device information settings.</span></span> <span data-ttu-id="289ae-180">Para obtener más información, consulte [PDF Device Information Settings](../pdf-device-information-settings.md).</span><span class="sxs-lookup"><span data-stu-id="289ae-180">For more information, see [PDF Device Information Settings](../pdf-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="289ae-181">Consulte también</span><span class="sxs-lookup"><span data-stu-id="289ae-181">See Also</span></span>  
 <span data-ttu-id="289ae-182">[Paginación en Reporting Services &#40;Generador de informes y SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="289ae-182">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="289ae-183">[Comportamientos de representación &#40;Generador de informes y SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="289ae-183">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="289ae-184">[Funcionalidad interactiva para diferentes extensiones de representación de informes &#40;Generador de informes y SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="289ae-184">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="289ae-185">[Representar elementos de informe &#40;Generador de informes y SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="289ae-185">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="289ae-186">Tablas, matrices y listas &#40;Generador de informes y SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="289ae-186">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  