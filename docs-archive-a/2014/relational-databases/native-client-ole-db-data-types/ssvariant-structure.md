---
title: Estructura SSVARIANT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: rothja
ms.author: jroth
ms.openlocfilehash: ed05eec7f9029519c04341380b8e43abc3d443bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87669671"
---
# <a name="ssvariant-structure"></a><span data-ttu-id="a9d88-102">Estructura SSVARIANT</span><span class="sxs-lookup"><span data-stu-id="a9d88-102">SSVARIANT Structure</span></span>
  <span data-ttu-id="a9d88-103">La estructura `SSVARIANT`, que se define en sqlncli.h, corresponde a un valor DBTYPE_SQLVARIANT en el proveedor OLEDB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span><span class="sxs-lookup"><span data-stu-id="a9d88-103">The `SSVARIANT` structure, which is defined in sqlncli.h, corresponds to a DBTYPE_SQLVARIANT value in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLEDB provider.</span></span>  
  
 <span data-ttu-id="a9d88-104">`SSVARIANT` es una unión de discriminación.</span><span class="sxs-lookup"><span data-stu-id="a9d88-104">`SSVARIANT` is a discriminating union.</span></span> <span data-ttu-id="a9d88-105">Según el valor del miembro vt, el consumidor puede determinar qué miembro tiene que leerse.</span><span class="sxs-lookup"><span data-stu-id="a9d88-105">Depending on the value of the vt member, the consumer can determine which member to read.</span></span> <span data-ttu-id="a9d88-106">Los valores de vt se corresponden con tipos de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-106">vt values correspond to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="a9d88-107">Por lo tanto, la estructura `SSVARIANT` puede contener cualquier tipo de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a9d88-107">Therefore, the `SSVARIANT` structure can hold any SQL Server type.</span></span> <span data-ttu-id="a9d88-108">Para más información sobre la estructura de datos de los tipos de OLE DB estándar, consulte [Indicadores de tipo](https://go.microsoft.com/fwlink/?LinkId=122171).</span><span class="sxs-lookup"><span data-stu-id="a9d88-108">For more information about the data structure for standard OLE DB types, see [Type Indicators](https://go.microsoft.com/fwlink/?LinkId=122171).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9d88-109">Observaciones</span><span class="sxs-lookup"><span data-stu-id="a9d88-109">Remarks</span></span>  
 <span data-ttu-id="a9d88-110">Cuando DataTypeCompat==80, varios subtipos `SSVARIANT` se convierten en cadenas.</span><span class="sxs-lookup"><span data-stu-id="a9d88-110">When DataTypeCompat==80, several `SSVARIANT` subtypes become strings.</span></span> <span data-ttu-id="a9d88-111">Por ejemplo, los siguientes valores de vt se mostrarán en `SSVARIANT` como VT_SS_WVARSTRING:</span><span class="sxs-lookup"><span data-stu-id="a9d88-111">For example, the following vt values will appear in `SSVARIANT` as VT_SS_WVARSTRING:</span></span>  
  
-   <span data-ttu-id="a9d88-112">VT_SS_DATETIMEOFFSET</span><span class="sxs-lookup"><span data-stu-id="a9d88-112">VT_SS_DATETIMEOFFSET</span></span>  
  
-   <span data-ttu-id="a9d88-113">VT_SS_DATETIME2</span><span class="sxs-lookup"><span data-stu-id="a9d88-113">VT_SS_DATETIME2</span></span>  
  
-   <span data-ttu-id="a9d88-114">VT_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="a9d88-114">VT_SS_TIME2</span></span>  
  
-   <span data-ttu-id="a9d88-115">VT_SS_DATE</span><span class="sxs-lookup"><span data-stu-id="a9d88-115">VT_SS_DATE</span></span>  
  
 <span data-ttu-id="a9d88-116">Cuando DateTypeCompat == 0, estos tipos se mostrarán en su forma nativa.</span><span class="sxs-lookup"><span data-stu-id="a9d88-116">When DateTypeCompat == 0, these types will appear in their native form.</span></span>  
  
 <span data-ttu-id="a9d88-117">Para obtener más información acerca de SSPROP_INIT_DATATYPECOMPATIBILITY, vea [usar palabras clave de cadena de conexión con SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span><span class="sxs-lookup"><span data-stu-id="a9d88-117">For more information about SSPROP_INIT_DATATYPECOMPATIBILITY, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="a9d88-118">El archivo sqlncli.h contiene macros de acceso a tipos de datos variant que simplifican la eliminación de referencias a los tipos de miembro de la estructura `SSVARIANT`.</span><span class="sxs-lookup"><span data-stu-id="a9d88-118">The sqlncli.h file contains variant access macros that simplify dereferencing the member types in the `SSVARIANT` structure.</span></span> <span data-ttu-id="a9d88-119">Un ejemplo sería V_SS_DATETIMEOFFSET, que puede utilizarse tal y como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a9d88-119">An example is V_SS_DATETIMEOFFSET, which you can use as follows:</span></span>  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 <span data-ttu-id="a9d88-120">Para obtener el conjunto completo de macros de acceso para cada miembro de la estructura `SSVARIANT`, consulte el archivo sqlncli.hi.</span><span class="sxs-lookup"><span data-stu-id="a9d88-120">For the complete set of access macros for each member of the `SSVARIANT` structure, refer to the sqlncli.hi file.</span></span>  
  
 <span data-ttu-id="a9d88-121">En la siguiente tabla se describen los miembros de la estructura `SSVARIANT`:</span><span class="sxs-lookup"><span data-stu-id="a9d88-121">The following table describes the members of the `SSVARIANT` structure:</span></span>  
  
|<span data-ttu-id="a9d88-122">Miembro</span><span class="sxs-lookup"><span data-stu-id="a9d88-122">Member</span></span>|<span data-ttu-id="a9d88-123">Indicador de tipo OLE DB</span><span class="sxs-lookup"><span data-stu-id="a9d88-123">OLE DB type indicator</span></span>|<span data-ttu-id="a9d88-124">Tipo de datos de OLE DB C</span><span class="sxs-lookup"><span data-stu-id="a9d88-124">OLE DB C data type</span></span>|<span data-ttu-id="a9d88-125">Valor de vt</span><span class="sxs-lookup"><span data-stu-id="a9d88-125">vt value</span></span>|<span data-ttu-id="a9d88-126">Comentarios</span><span class="sxs-lookup"><span data-stu-id="a9d88-126">Comments</span></span>|  
|------------|---------------------------|------------------------|--------------|--------------|  
|<span data-ttu-id="a9d88-127">vt</span><span class="sxs-lookup"><span data-stu-id="a9d88-127">vt</span></span>|<span data-ttu-id="a9d88-128">SSVARTYPE</span><span class="sxs-lookup"><span data-stu-id="a9d88-128">SSVARTYPE</span></span>|||<span data-ttu-id="a9d88-129">Especifica el tipo de valor incluido en la estructura `SSVARIANT`.</span><span class="sxs-lookup"><span data-stu-id="a9d88-129">Specifies the type of value contained in the `SSVARIANT` struct.</span></span>|  
|<span data-ttu-id="a9d88-130">bTinyIntVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-130">bTinyIntVal</span></span>|<span data-ttu-id="a9d88-131">DBTYPE_UI1</span><span class="sxs-lookup"><span data-stu-id="a9d88-131">DBTYPE_UI1</span></span>|`BYTE`|`VT_SS_UI1`|<span data-ttu-id="a9d88-132">Admite el tipo de datos `tinyint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-132">Supports the `tinyint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-133">sShortIntVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-133">sShortIntVal</span></span>|<span data-ttu-id="a9d88-134">DBTYPE_I2</span><span class="sxs-lookup"><span data-stu-id="a9d88-134">DBTYPE_I2</span></span>|`SHORT`|`VT_SS_I2`|<span data-ttu-id="a9d88-135">Admite el tipo de datos `smallint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-135">Supports the `smallint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-136">lIntVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-136">lIntVal</span></span>|<span data-ttu-id="a9d88-137">DBTYPE_I4</span><span class="sxs-lookup"><span data-stu-id="a9d88-137">DBTYPE_I4</span></span>|`LONG`|`VT_SS_I4`|<span data-ttu-id="a9d88-138">Admite el tipo de datos `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-138">Supports the `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-139">llBigIntVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-139">llBigIntVal</span></span>|<span data-ttu-id="a9d88-140">DBTYPE_I8</span><span class="sxs-lookup"><span data-stu-id="a9d88-140">DBTYPE_I8</span></span>|`LARGE_INTEGER`|`VT_SS_I8`|<span data-ttu-id="a9d88-141">Admite el tipo de datos `bigint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-141">Supports the `bigint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-142">fltRealVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-142">fltRealVal</span></span>|<span data-ttu-id="a9d88-143">DBTYPE_R4</span><span class="sxs-lookup"><span data-stu-id="a9d88-143">DBTYPE_R4</span></span>|`float`|`VT_SS_R4`|<span data-ttu-id="a9d88-144">Admite el tipo de datos `real`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-144">Supports the `real`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-145">dblFloatVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-145">dblFloatVal</span></span>|<span data-ttu-id="a9d88-146">DBTYPE_R8</span><span class="sxs-lookup"><span data-stu-id="a9d88-146">DBTYPE_R8</span></span>|`double`|`VT_SS_R8`|<span data-ttu-id="a9d88-147">Admite el tipo de datos `float`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-147">Supports the `float`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-148">cyMoneyVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-148">cyMoneyVal</span></span>|<span data-ttu-id="a9d88-149">DBTYPE_CY</span><span class="sxs-lookup"><span data-stu-id="a9d88-149">DBTYPE_CY</span></span>|`LARGE_INTEGER`|<span data-ttu-id="a9d88-150">**VT_SS_MONEY VT_SS_SMALLMONEY**</span><span class="sxs-lookup"><span data-stu-id="a9d88-150">**VT_SS_MONEY VT_SS_SMALLMONEY**</span></span>|<span data-ttu-id="a9d88-151">Admite los `money` tipos de datos y **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a9d88-151">Supports the `money` and **smallmoney**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>|  
|<span data-ttu-id="a9d88-152">fBitVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-152">fBitVal</span></span>|<span data-ttu-id="a9d88-153">DBTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="a9d88-153">DBTYPE_BOOL</span></span>|`VARIANT_BOOL`|`VT_SS_BIT`|<span data-ttu-id="a9d88-154">Admite el tipo de datos `bit`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-154">Supports the `bit`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-155">rgbGuidVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-155">rgbGuidVal</span></span>|<span data-ttu-id="a9d88-156">DBTYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="a9d88-156">DBTYPE_GUID</span></span>|`GUID`|`VT_SS_GUID`|<span data-ttu-id="a9d88-157">Admite el tipo de datos `uniqueidentifier`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-157">Supports the `uniqueidentifier`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-158">numNumericVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-158">numNumericVal</span></span>|<span data-ttu-id="a9d88-159">DBTYPE_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="a9d88-159">DBTYPE_NUMERIC</span></span>|`DB_NUMERIC`|`VT_SS_NUMERIC`|<span data-ttu-id="a9d88-160">Admite el tipo de datos `numeric`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-160">Supports the `numeric`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-161">dDateVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-161">dDateVal</span></span>|<span data-ttu-id="a9d88-162">DBTYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="a9d88-162">DBTYPE_DATE</span></span>|`DBDATE`|`VT_SS_DATE`|<span data-ttu-id="a9d88-163">Admite el tipo de datos `date`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-163">Supports the `date`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>|  
|<span data-ttu-id="a9d88-164">tsDateTimeVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-164">tsDateTimeVal</span></span>|<span data-ttu-id="a9d88-165">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a9d88-165">DBTYPE_DBTIMESTAMP</span></span>|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|<span data-ttu-id="a9d88-166">Admite los tipos de datos `smalldatetime`, `datetime` y `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9d88-166">Supports the `smalldatetime`, `datetime`, and `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>|  
|<span data-ttu-id="a9d88-167">Time2Val</span><span class="sxs-lookup"><span data-stu-id="a9d88-167">Time2Val</span></span>|<span data-ttu-id="a9d88-168">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="a9d88-168">DBTYPE_DBTIME2</span></span>|`DBTIME2`|`VT_SS_TIME2`|<span data-ttu-id="a9d88-169">Admite el tipo de datos `time`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-169">Supports the `time`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span><br /><br /> <span data-ttu-id="a9d88-170">Incluye los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9d88-170">Includes the following members:</span></span><br /><br /> <span data-ttu-id="a9d88-171">*tTime2Val* ( `DBTIME2` )</span><span class="sxs-lookup"><span data-stu-id="a9d88-171">*tTime2Val* (`DBTIME2`)</span></span><br /><br /> <span data-ttu-id="a9d88-172">*bScale* ( `BYTE` ) especifica la escala para el valor de *tTime2Val* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-172">*bScale* (`BYTE`) Specifies the scale for *tTime2Val* value.</span></span>|  
|<span data-ttu-id="a9d88-173">DateTimeVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-173">DateTimeVal</span></span>|<span data-ttu-id="a9d88-174">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="a9d88-174">DBTYPE_DBTIMESTAMP</span></span>|`DBTIMESTAMP`|`VT_SS_DATETIME2`|<span data-ttu-id="a9d88-175">Admite el tipo de datos `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-175">Supports the `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span><br /><br /> <span data-ttu-id="a9d88-176">Incluye los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9d88-176">Includes the following members:</span></span><br /><br /> <span data-ttu-id="a9d88-177">*tsDataTimeVal* (DBTIMESTAMP)</span><span class="sxs-lookup"><span data-stu-id="a9d88-177">*tsDataTimeVal* (DBTIMESTAMP)</span></span><br /><br /> <span data-ttu-id="a9d88-178">*bScale* ( `BYTE` ) especifica la escala para el valor de *tsDataTimeVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-178">*bScale* (`BYTE`) Specifies the scale for *tsDataTimeVal* value.</span></span>|  
|<span data-ttu-id="a9d88-179">DateTimeOffsetVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-179">DateTimeOffsetVal</span></span>|<span data-ttu-id="a9d88-180">DBTYPE_DBTIMESTAMPOFSET</span><span class="sxs-lookup"><span data-stu-id="a9d88-180">DBTYPE_DBTIMESTAMPOFSET</span></span>|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|<span data-ttu-id="a9d88-181">Admite el tipo de datos `datetimeoffset`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d88-181">Supports the `datetimeoffset`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span><br /><br /> <span data-ttu-id="a9d88-182">Incluye los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9d88-182">Includes the following members:</span></span><br /><br /> <span data-ttu-id="a9d88-183">*tsoDateTimeOffsetVal* ( `DBTIMESTAMPOFFSET` )</span><span class="sxs-lookup"><span data-stu-id="a9d88-183">*tsoDateTimeOffsetVal* (`DBTIMESTAMPOFFSET`)</span></span><br /><br /> <span data-ttu-id="a9d88-184">*bScale* ( `BYTE` ) especifica la escala para el valor de *tsoDateTimeOffsetVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-184">*bScale* (`BYTE`) Specifies the scale for *tsoDateTimeOffsetVal* value.</span></span>|  
|<span data-ttu-id="a9d88-185">NCharVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-185">NCharVal</span></span>|<span data-ttu-id="a9d88-186">No hay indicador de tipo OLE DB correspondiente.</span><span class="sxs-lookup"><span data-stu-id="a9d88-186">No corresponding OLE DB type indicator.</span></span>|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|<span data-ttu-id="a9d88-187">Admite los `nchar` tipos de datos y **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a9d88-187">Supports the `nchar` and **nvarchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span><br /><br /> <span data-ttu-id="a9d88-188">Incluye los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9d88-188">Includes the following members:</span></span><br /><br /> <span data-ttu-id="a9d88-189">*sActualLength* ( `SHORT` ) especifica la longitud real de la cadena a la que apunta *pwchNCharVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-189">*sActualLength* (`SHORT`) Specifies the actual length for the string to which *pwchNCharVal* points.</span></span> <span data-ttu-id="a9d88-190">No incluye cero de terminación.</span><span class="sxs-lookup"><span data-stu-id="a9d88-190">Does not include terminating zero.</span></span><br /><br /> <span data-ttu-id="a9d88-191">*sMaxLength* ( `SHORT` ) especifica la longitud máxima de la cadena a la que apunta *pwchNCharVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-191">*sMaxLength* (`SHORT`) Specifies the maximum length for the string to which *pwchNCharVal* points.</span></span><br /><br /> <span data-ttu-id="a9d88-192">puntero *pwchNCharVal* ( `WCHAR` \* ) a la cadena.</span><span class="sxs-lookup"><span data-stu-id="a9d88-192">*pwchNCharVal* (`WCHAR` \*) Pointer to the string.</span></span><br /><br /> <span data-ttu-id="a9d88-193">Miembros no usados: *rgbReserved*, *dwReserved*y *pwchReserved*.</span><span class="sxs-lookup"><span data-stu-id="a9d88-193">Unused members: *rgbReserved*, *dwReserved*, and *pwchReserved*.</span></span>|  
|<span data-ttu-id="a9d88-194">CharVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-194">CharVal</span></span>|<span data-ttu-id="a9d88-195">No hay indicador de tipo OLE DB correspondiente.</span><span class="sxs-lookup"><span data-stu-id="a9d88-195">No corresponding OLE DB type indicator.</span></span>|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|<span data-ttu-id="a9d88-196">Admite los `char` tipos de datos y **VARCHAR** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a9d88-196">Supports the `char` and **varchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span><br /><br /> <span data-ttu-id="a9d88-197">Incluye los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9d88-197">Includes the following members:</span></span><br /><br /> <span data-ttu-id="a9d88-198">*sActualLength* ( `SHORT` ) especifica la longitud real de la cadena a la que apunta *pchCharVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-198">*sActualLength* (`SHORT`) Specifies the actual length for the string to which *pchCharVal* points.</span></span> <span data-ttu-id="a9d88-199">No incluye cero de terminación.</span><span class="sxs-lookup"><span data-stu-id="a9d88-199">Does not include terminating zero.</span></span><br /><br /> <span data-ttu-id="a9d88-200">*sMaxLength* ( `SHORT` ) especifica la longitud máxima de la cadena a la que apunta *pchCharVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-200">*sMaxLength* (`SHORT`) Specifies the maximum length for the string to which *pchCharVal* points.</span></span><br /><br /> <span data-ttu-id="a9d88-201">puntero *pchCharVal* ( `CHAR` \* ) a la cadena.</span><span class="sxs-lookup"><span data-stu-id="a9d88-201">*pchCharVal* (`CHAR` \*) Pointer to the string.</span></span><br /><br /> <span data-ttu-id="a9d88-202">Miembros no usados:</span><span class="sxs-lookup"><span data-stu-id="a9d88-202">Unused members:</span></span><br /><br /> <span data-ttu-id="a9d88-203">*rgbReserved*, *dwReserved* y *pwchReserved*.</span><span class="sxs-lookup"><span data-stu-id="a9d88-203">*rgbReserved*, *dwReserved*, and *pwchReserved*.</span></span>|  
|<span data-ttu-id="a9d88-204">BinaryVal</span><span class="sxs-lookup"><span data-stu-id="a9d88-204">BinaryVal</span></span>|<span data-ttu-id="a9d88-205">No hay indicador de tipo OLE DB correspondiente.</span><span class="sxs-lookup"><span data-stu-id="a9d88-205">No corresponding OLE DB type indicator.</span></span>|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|<span data-ttu-id="a9d88-206">Admite los `binary` tipos de datos y **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a9d88-206">Supports the `binary` and **varbinary**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span><br /><br /> <span data-ttu-id="a9d88-207">Incluye los miembros siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9d88-207">Includes the following members:</span></span><br /><br /> <span data-ttu-id="a9d88-208">*sActualLength* ( `SHORT` ) especifica la longitud real de los datos a los que apunta *prgbBinaryVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-208">*sActualLength* (`SHORT`) Specifies the actual length for the data to which *prgbBinaryVal* points.</span></span><br /><br /> <span data-ttu-id="a9d88-209">*sMaxLength* ( `SHORT` ) especifica la longitud máxima de los datos a los que apunta *prgbBinaryVal* .</span><span class="sxs-lookup"><span data-stu-id="a9d88-209">*sMaxLength* (`SHORT`) Specifies the maximum length for the data to which *prgbBinaryVal* points.</span></span><br /><br /> <span data-ttu-id="a9d88-210">puntero *prgbBinaryVal* ( `BYTE` \* ) a los datos binarios.</span><span class="sxs-lookup"><span data-stu-id="a9d88-210">*prgbBinaryVal* (`BYTE` \*) Pointer to the binary data.</span></span><br /><br /> <span data-ttu-id="a9d88-211">Miembro no usado: *dwReserved*.</span><span class="sxs-lookup"><span data-stu-id="a9d88-211">Unused member: *dwReserved*.</span></span>|  
|<span data-ttu-id="a9d88-212">TipoDesconocido</span><span class="sxs-lookup"><span data-stu-id="a9d88-212">UnknownType</span></span>|<span data-ttu-id="a9d88-213">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-213">UNUSED</span></span>|<span data-ttu-id="a9d88-214">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-214">UNUSED</span></span>|<span data-ttu-id="a9d88-215">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-215">UNUSED</span></span>|<span data-ttu-id="a9d88-216">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-216">UNUSED</span></span>|  
|<span data-ttu-id="a9d88-217">BLOBType</span><span class="sxs-lookup"><span data-stu-id="a9d88-217">BLOBType</span></span>|<span data-ttu-id="a9d88-218">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-218">UNUSED</span></span>|<span data-ttu-id="a9d88-219">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-219">UNUSED</span></span>|<span data-ttu-id="a9d88-220">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-220">UNUSED</span></span>|<span data-ttu-id="a9d88-221">No se usa</span><span class="sxs-lookup"><span data-stu-id="a9d88-221">UNUSED</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9d88-222">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a9d88-222">See Also</span></span>  
 [<span data-ttu-id="a9d88-223">Tipos de datos &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a9d88-223">Data Types &#40;OLE DB&#41;</span></span>](data-types-ole-db.md)  
  
  