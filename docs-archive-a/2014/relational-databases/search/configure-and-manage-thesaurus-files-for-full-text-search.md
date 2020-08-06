---
title: Configurar y administrar archivos de sinónimos para búsquedas de texto completo | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67f0a5af7be4f41ce33692e5f28ad5adf676980c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87752081"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a>Configurar y administrar archivos de sinónimos para búsquedas de texto completo
  En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], las consultas de texto completo pueden buscar sinónimos de los términos especificados por el usuario usando un diccionario de sinónimos. Un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *de* define un conjunto de sinónimos para un idioma concreto. Los administradores del sistema pueden definir dos formatos de sinónimos: conjuntos de expansión y conjuntos de reemplazo. Al desarrollar un diccionario de sinónimos personalizado para los datos de texto completo, puede ampliar de forma eficaz el ámbito de las consultas de texto completo en esos datos. La comprobación de coincidencia con el diccionario de sinónimos tiene lugar para todas las consultas [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) y [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) , y para las consultas [CONTAINS](/sql/t-sql/queries/contains-transact-sql) y [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) que especifican la cláusula FORMSOF THESAURUS.  
  
##  <a name="basic-tasks-for-setting-up-a-thesaurus-file"></a><a name="tasks"></a>Tareas básicas para configurar un archivo de sinónimos  
 Para que las consultas de búsqueda de texto completo en la instancia de servidor puedan buscar sinónimos en un idioma determinado, debe definir las asignaciones del diccionario de sinónimos de ese idioma. Cada diccionario de sinónimos se debe configurar manualmente para definir lo siguiente:  
  
-   Configuración de signos diacríticos  
  
     Para un diccionario de sinónimos determinado, todos los patrones de búsqueda son confidenciales o no distinguen entre marcas diacríticas como una tilde ( **~** ), acento agudo (**??**) o umlaut (**??**) (es decir, con *distinción de acentos* o sin *distinción de acentos*). Por ejemplo, supongamos que especifica el patrón "cafetería??". para que se reemplace por otros patrones en una consulta de texto completo. Si el Diccionario de sinónimos no distingue acentos, la búsqueda de texto completo reemplaza los patrones "cafetería??" y "cafe". Si el Diccionario de sinónimos distingue acentos, la búsqueda de texto completo solo reemplaza el patrón "cafetería??". De forma predeterminada, un diccionario de sinónimos no distingue acentos.  
  
-   Conjunto de expansión  
  
     Un conjunto de expansión contiene un grupo de sinónimos como "escritor", "autor" y "periodista" que se sustituyen entre si en una consulta de texto completo. Las consultas que contienen una coincidencia para algún sinónimo en un conjunto de expansión se expanden para incluir uno de cada dos sinónimos en el conjunto de expansión.  
  
     Para obtener más información, vea "Estructura XML de un conjunto de expansión", posteriormente en este tema.  
  
-   Conjunto de reemplazo  
  
     Un conjunto de reemplazo contiene un patrón de texto que se reemplazará por un conjunto de sustitución. Para obtener un ejemplo, vea la sección "Estructura XML de un conjunto de reemplazo" más adelante en este tema.  
  
  
##  <a name="initial-content-of-the-thesaurus-files"></a><a name="initial_thesaurus_files"></a>Contenido inicial de los archivos de sinónimos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona un conjunto de archivos de sinónimos XML, uno para cada idioma admitido. Estos archivos están esencialmente vacíos. Contienen solo la estructura XML de nivel superior que es común a todos los diccionarios de sinónimos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y un diccionario de sinónimos de ejemplo como comentario.  
  
 Los archivos de sinónimos que se publican con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contienen el siguiente código XML:  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location-of-the-thesaurus-files"></a><a name="location"></a>Ubicación de los archivos de sinónimos  
 La ubicación predeterminada de los archivos de sinónimos es la siguiente:  
  
 *<SQL_Server_data_files_path>* \MSSQL12. MSSQLSERVER\MSSQL\FTDATA\  
  
 Esta ubicación predeterminada contiene los archivos siguientes:  
  
-   Archivos de sinónimos específicos del idioma  
  
     Durante la instalación, los archivos de sinónimos vacíos se instalan en la ubicación anterior. Se proporciona un archivo independiente para cada idioma admitido. Un administrador del sistema puede personalizar estos archivos.  
  
     Los nombres de archivo predeterminados de los archivos de sinónimos usan el formato siguiente:  
  
     ' ts ' + \<three-letter language-abbreviation> + '. xml '  
  
     El nombre del archivo de diccionario de sinónimos para un idioma dado se especifica en el Registro en el valor siguiente: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev>.  
  
-   El archivo de sinónimos global  
  
     Un archivo de sinónimos global y vacío, tsGlobal.xml.  
  
 Puede cambiar la ubicación y los nombres de un archivo de sinónimos cambiando su clave del Registro. Para cada idioma, la ubicación del archivo de sinónimos se especifica en el valor siguiente en el Registro:  
  
 HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/ \<instance name> /MSSearch/Language/ \<language-abbreviation> /TsaurusFile  
  
 El archivo de sinónimos global corresponde al idioma neutro con el LCID 0. Solo los administradores pueden cambiar este valor.  
  
  
##  <a name="how-queries-use-thesaurus-files"></a><a name="how_queries_use_tf"></a>Cómo usan los archivos de sinónimos las consultas  
 Una consulta del diccionario de sinónimos utiliza un diccionario de sinónimos específico del idioma y el diccionario de sinónimos global. Primero, la consulta busca el archivo específico del idioma y lo carga para su procesamiento (a menos que ya esté cargado). La consulta se expande para incluir los sinónimos específicos del idioma especificados por las reglas de conjuntos de expansión y conjuntos de reemplazo en el archivo de diccionario de sinónimos. Estos pasos se repiten después para el diccionario de sinónimos global. Sin embargo, si un término ya forma parte de una coincidencia en el archivo de diccionario de sinónimos específico del idioma, el término es ilegible para coincidencias en el diccionario de sinónimos global.  
  
  
##  <a name="understanding-the-structure-of-a-thesaurus-file"></a><a name="structure"></a>Descripción de la estructura de un archivo de Diccionario de sinónimos  
 Cada archivo de sinónimos define un contenedor XML cuyo identificador es `Microsoft Search Thesaurus` y un comentario, `<!--` ... `-->`, que contiene un diccionario de sinónimos de ejemplo. El Diccionario de sinónimos se define en un \<thesaurus> elemento que contiene ejemplos de los elementos secundarios que definen la configuración de los signos diacríticos, los conjuntos de expansión y los conjuntos de reemplazo, como se indica a continuación:  
  
-   Estructura XML de la configuración de signos diacríticos  
  
     La configuración de signos diacríticos de un diccionario de sinónimos se especifica en un único elemento <diacritics_sensitive>. Este elemento contiene un valor entero que controla la distinción de acentos, de la forma siguiente:  
  
    |Configuración de signos diacríticos|Value|XML|  
    |------------------------|-----------|---------|  
    |no distinguen acentos|0|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |distinguen acentos|1|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  Esta configuración solo se puede aplicar una vez en el archivo, y se aplica a todos los patrones de búsqueda del mismo. Esta configuración no se puede especificar para patrones individuales.  
  
-   Estructura XML de un conjunto de expansión  
  
     Cada conjunto de expansión está delimitado por un elemento \<expansion>. Dentro de este elemento, se especifican una o varias sustituciones en un elemento \<sub>. En el conjunto de expansión, puede especificar un grupo de sustituciones que sean sinónimas.  
  
     Por ejemplo, puede editar la sección de expansión para tratar las sustituciones "writer", "author" y "journalist" como sinónimos. Las consultas de búsqueda de texto completo que contienen coincidencias en una sustitución se expanden para incluir todas las demás sustituciones especificadas en el conjunto de expansión. Por tanto, en el ejemplo anterior, al emitir una consulta FORMS OF THESAURUS o FREETEXT para la palabra "autor", la búsqueda de texto completo también devuelve resultados que contienen las palabras "escritor" y "periodista".  
  
     Esta es la apariencia que tendrá la sección del conjunto de expansión en el caso del ejemplo anterior:  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   Estructura XML de un conjunto de reemplazo  
  
     Cada conjunto de reemplazo está delimitado por un elemento \<replacement>. Dentro de este elemento, se pueden especificar uno o varios modelos en un elemento \<pat> y cero o más sustituciones en elementos \<sub>, una por cada sinónimo. Puede especificar un patrón para que sea reemplazado por un conjunto de sustitución. Los patrones y las sustituciones pueden contener una palabra o una secuencia de palabras. Si no se especifica ninguna sustitución para un modelo, se quita el modelo de la consulta del usuario.  
  
     Por ejemplo, imagine que desea que las consultas de "Win8", el patrón, sean reemplazadas por "Windows Server 2012" o "Windows 8.0", las sustituciones. Si ejecuta una búsqueda de texto completo de "Win8", solo devolverá los resultados que contengan "Windows Server 2012" o "Windows 8.0". No devolverá resultados que contengan "Win8". Esto se debe a que el patrón "Win8" ha sido "reemplazado" por los patrones "Windows Server 2012" y "Windows 8.0".  
  
     Éste es el aspecto que tendrá la sección del conjunto de reemplazo en el caso del ejemplo anterior:  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     Si tiene dos conjuntos de reemplazo con patrones similares para los que se buscan coincidencias, prevalecerá el más largo de los dos. Por ejemplo, si ejecuta una consulta FORMS OF THESAURUS para "Comunidad en línea de Internet Explorer" y tiene los siguientes conjuntos de reemplazo, el conjunto de reemplazo "Internet Explorer" tiene prioridad sobre el conjunto de reemplazo "Internet". Por tanto, la consulta se procesará como "Comunidad en línea de IE" o "Comunidad en línea de IE 9".  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     y  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working-with-thesaurus-files"></a><a name="working_with_thesaurus_files"></a>Trabajar con archivos de sinónimos  
 **Modificar un archivo de sinónimos**  
  
-   [Editar un archivo de sinónimos](#editing)  
  
 **Cargar un archivo de sinónimos actualizado**  
  
-   [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 **Para ver el resultado de la tokenización de una combinación entre un separador de palabras, un diccionario de sinónimos y una lista de palabras irrelevantes**  
  
-   [Sys. dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing-a-thesaurus-file"></a><a name="editing"></a>Editar un archivo de Diccionario de sinónimos  
 El diccionario de sinónimos de un idioma determinado se puede configurar modificando su archivo de diccionario de sinónimos (un archivo XML). Durante la instalación, se instalan los archivos de Diccionario de sinónimos vacíos que contienen solo el \<xml> contenedor y un elemento de ejemplo comentado como comentario \<thesaurus> . Para que las consultas de búsqueda de texto completo que buscan sinónimos funcionen correctamente, debe crear un elemento real \<thesaurus> que defina un conjunto de sinónimos. Puede definir dos formatos de sinónimos: conjuntos de expansión y conjuntos de reemplazo.  
  
 **Restricciones de los archivos de diccionarios de sinónimos**  
  
 Las restricciones siguientes se aplican al modificar un archivo de diccionario de sinónimos:  
  
-   Solo los administradores del sistema pueden actualizar, modificar o eliminar archivos de diccionarios de sinónimos.  
  
-   Al modificar archivos de diccionarios de sinónimos con herramientas de edición de texto, los archivos deben guardarse en formato Unicode y deben especificarse marcas de orden de bytes.  
  
-   Las entradas del diccionario de sinónimos no pueden estar vacías ni tener separación de palabras en una cadena vacía.  
  
-   Las frases del archivo de diccionario de sinónimos no deben tener más de 512 caracteres.  
  
-   Un diccionario de sinónimos no debe contener ninguna entrada duplicada entre las entradas \<sub> de los conjuntos de expansión y los elementos \<pat> de los conjuntos de reemplazo.  
  
 **Recomendaciones para los archivos de diccionarios de sinónimos**  
  
 Se recomienda que las entradas del archivo de diccionario de sinónimos no contengan ningún carácter especial. Esto se debe a que los separadores de palabras demuestran comportamientos sutiles con respecto a los caracteres especiales. Si una entrada del diccionario de sinónimos contiene algún carácter especial, los separadores de palabras que se usan en combinación con esa entrada pueden tener implicaciones sutiles de comportamiento en una consulta de texto completo.  
  
 Se recomienda que las entradas \<sub> no contengan palabras irrelevantes porque estas se omiten en el índice de texto completo. Las consultas se expanden para incluir las entradas \<sub> de un archivo de diccionario de sinónimos y, si una entrada \<sub> contiene palabras irrelevantes, el tamaño de la consulta aumenta innecesariamente.  
  
#### <a name="to-edit-a-thesaurus-file"></a>Modificar un archivo de sinónimos  
  
1.  Abra el archivo de diccionario de sinónimos en el Bloc de notas.  
  
2.  Si va a modificar el archivo de sinónimos por primera vez, quite las siguientes líneas de comentarios del principio y el final del archivo, respectivamente:  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  Agregue, modifique o elimine un conjunto de reemplazo o un conjunto de expansión.  
  
4.  Guarde el archivo y cierre el Bloc de notas.  
  
5.  Use [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) para cargar el contenido del archivo de diccionario de sinónimos en tempdb, especificando el identificador local (LCID) que corresponde al idioma del archivo de diccionario de sinónimos. Por ejemplo, para el archivo de diccionario de sinónimos en inglés, tsenu.xml, el LCID correspondiente es 1033.  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a>Consulte también  
 [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)   
 [Búsqueda de texto completo](full-text-search.md)  
  
  
