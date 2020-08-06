---
title: srv_convert (API de procedimiento almacenado extendido) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_convert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_convert
ms.assetid: 216b4a31-786e-4361-8a33-e5f6e9790f90
author: rothja
ms.author: jroth
ms.openlocfilehash: 30a0ea356f017ed3d1b3ecc85cf483b4553e120a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87677106"
---
# <a name="srv_convert-extended-stored-procedure-api"></a>srv_convert (API de procedimiento almacenado extendido)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use la integración con CLR en su lugar.  
  
 Cambia los datos de un tipo de datos a otro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int srv_convert (  
SRV_PROC *  
srvproc  
,  
int  
srctype  
,  
void *  
src  
,  
DBINT  
srclen  
,  
int  
desttype  
,  
void *  
dest  
,  
DBINT  
destlen  
);  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 Es un puntero a la estructura SRV_PROC que es el identificador de una conexión cliente determinada. La estructura contiene toda la información de control que Procedimiento almacenado extendido usa para administrar las comunicaciones y los datos entre la aplicación y el cliente. Si se proporciona el identificador *srvproc*, se pasa a la función del controlador de errores de la API de procedimiento almacenado extendido cuando se produce un error.  
  
 *srctype*  
 Especifica el tipo de datos de los datos que se van a convertir. Este parámetro puede ser cualquiera de los tipos de datos de API Procedimiento almacenado extendido.  
  
 *src*  
 Es un puntero a los datos que se van a convertir. Este parámetro puede ser cualquiera de los tipos de datos de API Procedimiento almacenado extendido.  
  
 *srclen*  
 Especifica la longitud, en bytes, de los datos que se van a convertir. Si *srclen* es 0, **srv_convert** coloca un valor NULL en la variable de destino. A menos que sea 0, los tipos de datos de longitud fija pasan por alto este parámetro, en cuyo caso se supone que los datos de origen son NULL. Para los datos del tipo de datos SRVCHAR, una longitud de -1 indica que la cadena termina en NULL.  
  
 *desttype*  
 Especifica el tipo de datos para convertir el origen. Este parámetro puede ser cualquiera de los tipos de datos de API Procedimiento almacenado extendido.  
  
 *dest*  
 Es un puntero a la variable de destino que recibe los datos convertidos. Si este puntero es NULL, **srv_convert** llama al controlador de errores proporcionado por el usuario, si lo hubiera, y devuelve -1.  
  
 Si *desttype* es SRVDECIMAL o SRVNUMERIC, el parámetro *dest* debe ser un puntero a una estructura DBNUMERIC o DBDECIMAL con los campos de escala y precisión de la estructura ya establecidos en los valores deseados. Puede usar DEFAULTPRECISION para especificar una precisión predeterminada y DEFAULTSCALE para especificar una escala predeterminada.  
  
 *destlen*  
 Especifica la longitud, en bytes, de la variable de destino. Este parámetro se pasa por alto en los tipos de datos de longitud fija. Para una variable de destino de tipo SRVCHAR, el valor de *destlen* debe ser la longitud total del espacio en búfer de destino. Una longitud de -1 para una variable de destino de tipo SRVCHAR o SRVBINARY indica que hay suficiente espacio disponible. Para una variable de destino de tipo *srvchar*, una longitud de -1 hace que la cadena de caracteres termine en NULL.  
  
## <a name="returns"></a>Devoluciones  
 La longitud de los datos convertidos, en bytes, si la conversión de tipos de datos es correcta. Cuando **srv_convert** encuentra una solicitud de conversión que no admite, llama al controlador de errores proporcionado por el desarrollador, si lo hubiera, establece un número de error global y devuelve -1.  
  
## <a name="remarks"></a>Observaciones  
 La función **srv_willconvert** determina si se permite una conversión determinada.  
  
 La conversión a los tipos de datos numéricos aproximados SRVFLT4 o SRVFLT8 puede producir alguna pérdida de precisión. La conversión de los tipos de datos numéricos aproximados SRVFLT4 o SRVFLT8 a SRVCHAR o SRVTEXT también puede producir alguna pérdida de precisión.  
  
 La conversión a SRVFLT*x*, SRVINT*x*, SRVMONEY, SRVMONEY4, SRVDECIMAL o SRVNUMERIC puede producir un desbordamiento si el número es mayor que el valor máximo del destino, o un subdesbordamiento si el número es menor que el valor mínimo del destino. Si el desbordamiento se produce al convertir a SRVCHAR o SRVTEXT, el primer carácter del valor resultante contiene un asterisco (*) que indica el error.  
  
 Al convertir SRVCHAR en SRVBINARY, **srv_convert** interpreta SRVCHAR como hexadecimal, tanto si la cadena contiene un 0 inicial como si no. Al convertir SRVBINARY en SRVCHAR, **srv_convert** crea una cadena hexadecimal sin un 0 inicial. En todos los otros casos, una conversión a o desde el tipo de datos SRVBINARY es una copia de bits directa.  
  
 En ciertos casos, puede ser útil para convertir un tipo de datos en sí mismo. Por ejemplo, al convertir SRVCHAR en SRVCHAR con un valor *destlen* de -1, se agrega un terminador NULL a una cadena.  
  
 Para obtener una descripción de tipos de datos y conversiones de tipos de datos de API de procedimiento almacenado extendido, vea [Data Types &#40;Extended Stored Procedure API&#41; (Tipos de datos &#40;API de procedimiento almacenado extendido&#41;)](data-types-extended-stored-procedure-api.md).  
  
 Se puede producir un error en la función **srv_convert** por varias razones:  
  
-   La conversión solicitada no está disponible.  
  
-   La conversión producía el truncamiento, desbordamiento o pérdida de precisión en la variable de destino.  
  
-   Se produjo un error de sintaxis al convertir una cadena de caracteres en un tipo de datos numéricos.  
  
> [!IMPORTANT]  
>  Debe revisar minuciosamente el código fuente de los procedimientos almacenados extendidos y debe probar las DLL compiladas antes de instalarlas en el servidor de producción. Para obtener información acerca de la revisión y pruebas de seguridad, vea este [sitio web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Consulte también  
 [srv_setutype API de procedimiento almacenado extendido &#40;&#41;](srv-setutype-extended-stored-procedure-api.md)   
 [srv_willconvert &#40;API de procedimiento almacenado extendido&#41;](srv-willconvert-extended-stored-procedure-api.md)  
  
  
