---
title: Clase de eventos Broker:Remote Message Ack | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Remote Message Ack event class
ms.assetid: 3d67efe1-74b4-4633-b029-c6e05b19f4dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8be728cb865329d33367c727af862fdba1c87a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663528"
---
# <a name="brokerremote-message-ack-event-class"></a><span data-ttu-id="64495-102">Broker:Remote Message Ack, clase de eventos</span><span class="sxs-lookup"><span data-stu-id="64495-102">Broker:Remote Message Ack Event Class</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="64495-103">genera un evento **Broker:Remote Message Ack** cuando [!INCLUDE[ssSB](../../includes/sssb-md.md)] envía o recibe un reconocimiento de mensaje.</span><span class="sxs-lookup"><span data-stu-id="64495-103">generates a **Broker:Remote Message Ack** event when [!INCLUDE[ssSB](../../includes/sssb-md.md)] sends or receives a message acknowledgement.</span></span>  
  
## <a name="brokerremote-message-ack-event-class-data-columns"></a><span data-ttu-id="64495-104">Columnas de datos de la clase de eventos Broker:Remote Message Ack</span><span class="sxs-lookup"><span data-stu-id="64495-104">Broker:Remote Message Ack Event Class Data Columns</span></span>  
  
|<span data-ttu-id="64495-105">Columna de datos</span><span class="sxs-lookup"><span data-stu-id="64495-105">Data column</span></span>|<span data-ttu-id="64495-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="64495-106">Type</span></span>|<span data-ttu-id="64495-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="64495-107">Description</span></span>|<span data-ttu-id="64495-108">Número de columna</span><span class="sxs-lookup"><span data-stu-id="64495-108">Column number</span></span>|<span data-ttu-id="64495-109">Filtrable</span><span class="sxs-lookup"><span data-stu-id="64495-109">Filterable</span></span>|  
|-----------------|----------|-----------------|-------------------|----------------|  
|<span data-ttu-id="64495-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="64495-110">**ApplicationName**</span></span>|<span data-ttu-id="64495-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64495-111">**nvarchar**</span></span>|<span data-ttu-id="64495-112">Nombre de la aplicación cliente que ha creado la conexión a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="64495-112">The name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="64495-113">Esta columna se rellena con los valores que pasa la aplicación en lugar de con el nombre mostrado del programa.</span><span class="sxs-lookup"><span data-stu-id="64495-113">This column is populated with the values that are  passed by the application, instead of the displayed name of the program.</span></span>|<span data-ttu-id="64495-114">10</span><span class="sxs-lookup"><span data-stu-id="64495-114">10</span></span>|<span data-ttu-id="64495-115">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-115">Yes</span></span>|  
|<span data-ttu-id="64495-116">**BigintData1**</span><span class="sxs-lookup"><span data-stu-id="64495-116">**BigintData1**</span></span>|<span data-ttu-id="64495-117">**bigint**</span><span class="sxs-lookup"><span data-stu-id="64495-117">**bigint**</span></span>|<span data-ttu-id="64495-118">Número de secuencia del mensaje que contiene el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="64495-118">The sequence number of the message that contains the acknowledgement.</span></span>|<span data-ttu-id="64495-119">52</span><span class="sxs-lookup"><span data-stu-id="64495-119">52</span></span>|<span data-ttu-id="64495-120">No</span><span class="sxs-lookup"><span data-stu-id="64495-120">No</span></span>|  
|<span data-ttu-id="64495-121">**BigintData2**</span><span class="sxs-lookup"><span data-stu-id="64495-121">**BigintData2**</span></span>|<span data-ttu-id="64495-122">**bigint**</span><span class="sxs-lookup"><span data-stu-id="64495-122">**bigint**</span></span>|<span data-ttu-id="64495-123">Número de secuencia del mensaje que se va a reconocer.</span><span class="sxs-lookup"><span data-stu-id="64495-123">The sequence number of the message that is being acknowledged.</span></span>|<span data-ttu-id="64495-124">53</span><span class="sxs-lookup"><span data-stu-id="64495-124">53</span></span>|<span data-ttu-id="64495-125">No</span><span class="sxs-lookup"><span data-stu-id="64495-125">No</span></span>|  
|<span data-ttu-id="64495-126">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="64495-126">**ClientProcessID**</span></span>|<span data-ttu-id="64495-127">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-127">**int**</span></span>|<span data-ttu-id="64495-128">Id. que el equipo host asigna al proceso en el que se ejecuta la aplicación cliente.</span><span class="sxs-lookup"><span data-stu-id="64495-128">The ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="64495-129">Esta columna de datos se rellena si el cliente proporciona su identificador de proceso.</span><span class="sxs-lookup"><span data-stu-id="64495-129">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="64495-130">9</span><span class="sxs-lookup"><span data-stu-id="64495-130">9</span></span>|<span data-ttu-id="64495-131">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-131">Yes</span></span>|  
|<span data-ttu-id="64495-132">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="64495-132">**DatabaseID**</span></span>|<span data-ttu-id="64495-133">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-133">**int**</span></span>|<span data-ttu-id="64495-134">Id. de la base de datos especificada por la instrucción USE *database* .</span><span class="sxs-lookup"><span data-stu-id="64495-134">The ID of the database that is specified by the USE *database* statement.</span></span> <span data-ttu-id="64495-135">Si no se emitió ninguna instrucción USE *database* para una instancia determinada, el identificador de la base de datos predeterminada.</span><span class="sxs-lookup"><span data-stu-id="64495-135">If no USE *database* statement has been issued for a given instance, the ID of the default database.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="64495-136">muestra el nombre de la base de datos si se captura la columna de datos **ServerName** en el seguimiento y el servidor está disponible.</span><span class="sxs-lookup"><span data-stu-id="64495-136">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="64495-137">Determina el valor de una base de datos mediante la función DB_ID.</span><span class="sxs-lookup"><span data-stu-id="64495-137">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="64495-138">3</span><span class="sxs-lookup"><span data-stu-id="64495-138">3</span></span>|<span data-ttu-id="64495-139">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-139">Yes</span></span>|  
|<span data-ttu-id="64495-140">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="64495-140">**EventClass**</span></span>|<span data-ttu-id="64495-141">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-141">**int**</span></span>|<span data-ttu-id="64495-142">Tipo de clase de eventos capturado.</span><span class="sxs-lookup"><span data-stu-id="64495-142">The type of event class captured.</span></span> <span data-ttu-id="64495-143">Es siempre **149** para **Broker:Message Ack**.</span><span class="sxs-lookup"><span data-stu-id="64495-143">Always **149** for **Broker:Message Ack**.</span></span>|<span data-ttu-id="64495-144">27</span><span class="sxs-lookup"><span data-stu-id="64495-144">27</span></span>|<span data-ttu-id="64495-145">No</span><span class="sxs-lookup"><span data-stu-id="64495-145">No</span></span>|  
|<span data-ttu-id="64495-146">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="64495-146">**EventSequence**</span></span>|<span data-ttu-id="64495-147">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-147">**int**</span></span>|<span data-ttu-id="64495-148">Número de secuencia de este evento.</span><span class="sxs-lookup"><span data-stu-id="64495-148">Sequence number for this event.</span></span>|<span data-ttu-id="64495-149">51</span><span class="sxs-lookup"><span data-stu-id="64495-149">51</span></span>|<span data-ttu-id="64495-150">No</span><span class="sxs-lookup"><span data-stu-id="64495-150">No</span></span>|  
|<span data-ttu-id="64495-151">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="64495-151">**EventSubClass**</span></span>|<span data-ttu-id="64495-152">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64495-152">**nvarchar**</span></span>|<span data-ttu-id="64495-153">Tipo de subclase de evento, que proporciona más información acerca de cada clase de eventos.</span><span class="sxs-lookup"><span data-stu-id="64495-153">The type of event subclass, providing more information about each event class.</span></span> <span data-ttu-id="64495-154">Esta columna puede incluir los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="64495-154">This column can contain the following values:</span></span><br /><br /> <span data-ttu-id="64495-155">**Mensaje con confirmación enviada**</span><span class="sxs-lookup"><span data-stu-id="64495-155">**Message With Acknowledgement Sent**</span></span><br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="64495-156">se ha enviado un reconocimiento como parte de un mensaje en secuencia normal.</span><span class="sxs-lookup"><span data-stu-id="64495-156">sent an acknowledgement as part of a normal sequenced message.</span></span><br /><br /> <span data-ttu-id="64495-157">**Confirmación enviada**</span><span class="sxs-lookup"><span data-stu-id="64495-157">**Acknowledgement Sent**</span></span><br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="64495-158">se ha enviado un reconocimiento fuera de un mensaje en secuencia normal.</span><span class="sxs-lookup"><span data-stu-id="64495-158">sent an acknowledgement outside a normal sequenced message.</span></span><br /><br /> <span data-ttu-id="64495-159">**Mensaje con confirmación recibida**</span><span class="sxs-lookup"><span data-stu-id="64495-159">**Message With Acknowledgement Received**</span></span><br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="64495-160">se ha recibido un reconocimiento como parte de un mensaje en secuencia normal.</span><span class="sxs-lookup"><span data-stu-id="64495-160">received an acknowledgement as part of a normal sequenced message.</span></span><br /><br /> <span data-ttu-id="64495-161">**Confirmación recibida**</span><span class="sxs-lookup"><span data-stu-id="64495-161">**Acknowledgement Received**</span></span><br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="64495-162">se ha recibido un reconocimiento fuera de un mensaje en secuencia normal.</span><span class="sxs-lookup"><span data-stu-id="64495-162">received an acknowledgement outside a sequenced message.</span></span>|<span data-ttu-id="64495-163">21</span><span class="sxs-lookup"><span data-stu-id="64495-163">21</span></span>|<span data-ttu-id="64495-164">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-164">Yes</span></span>|  
|<span data-ttu-id="64495-165">**GUID**</span><span class="sxs-lookup"><span data-stu-id="64495-165">**GUID**</span></span>|<span data-ttu-id="64495-166">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="64495-166">**uniqueidentifier**</span></span>|<span data-ttu-id="64495-167">Id. de conversación del diálogo.</span><span class="sxs-lookup"><span data-stu-id="64495-167">The conversation ID of the dialog.</span></span> <span data-ttu-id="64495-168">Este identificador se transmite como parte del mensaje y lo comparten ambas partes de la conversación.</span><span class="sxs-lookup"><span data-stu-id="64495-168">This identifier is transmitted as part of the message, and is shared between both sides of the conversation.</span></span>|<span data-ttu-id="64495-169">54</span><span class="sxs-lookup"><span data-stu-id="64495-169">54</span></span>|<span data-ttu-id="64495-170">No</span><span class="sxs-lookup"><span data-stu-id="64495-170">No</span></span>|  
|<span data-ttu-id="64495-171">**HonorBrokerPriority**</span><span class="sxs-lookup"><span data-stu-id="64495-171">**HonorBrokerPriority**</span></span>|<span data-ttu-id="64495-172">**Int**</span><span class="sxs-lookup"><span data-stu-id="64495-172">**Int**</span></span>|<span data-ttu-id="64495-173">Valor actual de la opción HONOR_BROKER_PRIORITY de la base de datos: 0 = OFF, 1 = ON.</span><span class="sxs-lookup"><span data-stu-id="64495-173">The current value of the database HONOR_BROKER_PRIORITY option: 0 = OFF, 1 = ON.</span></span>|<span data-ttu-id="64495-174">32</span><span class="sxs-lookup"><span data-stu-id="64495-174">32</span></span>|<span data-ttu-id="64495-175">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-175">Yes</span></span>|  
|<span data-ttu-id="64495-176">**HostName**</span><span class="sxs-lookup"><span data-stu-id="64495-176">**HostName**</span></span>|<span data-ttu-id="64495-177">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64495-177">**nvarchar**</span></span>|<span data-ttu-id="64495-178">Nombre del equipo en el que se está ejecutando el cliente.</span><span class="sxs-lookup"><span data-stu-id="64495-178">The name of the computer on which the client is running.</span></span> <span data-ttu-id="64495-179">Esta columna de datos se rellena si el cliente proporciona el nombre del host.</span><span class="sxs-lookup"><span data-stu-id="64495-179">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="64495-180">Para determinar el nombre del host, utilice la función HOST_NAME.</span><span class="sxs-lookup"><span data-stu-id="64495-180">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="64495-181">8</span><span class="sxs-lookup"><span data-stu-id="64495-181">8</span></span>|<span data-ttu-id="64495-182">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-182">Yes</span></span>|  
|<span data-ttu-id="64495-183">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="64495-183">**IntegerData**</span></span>|<span data-ttu-id="64495-184">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-184">**int**</span></span>|<span data-ttu-id="64495-185">Número de fragmento del mensaje que contiene el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="64495-185">The fragment number of the message that contains the acknowledgement.</span></span>|<span data-ttu-id="64495-186">25</span><span class="sxs-lookup"><span data-stu-id="64495-186">25</span></span>|<span data-ttu-id="64495-187">No</span><span class="sxs-lookup"><span data-stu-id="64495-187">No</span></span>|  
|<span data-ttu-id="64495-188">**IntegerData2**</span><span class="sxs-lookup"><span data-stu-id="64495-188">**IntegerData2**</span></span>|<span data-ttu-id="64495-189">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-189">**int**</span></span>|<span data-ttu-id="64495-190">Número de fragmento del mensaje que se va a reconocer.</span><span class="sxs-lookup"><span data-stu-id="64495-190">The fragment number of the message being acknowledged.</span></span>|<span data-ttu-id="64495-191">55</span><span class="sxs-lookup"><span data-stu-id="64495-191">55</span></span>|<span data-ttu-id="64495-192">No</span><span class="sxs-lookup"><span data-stu-id="64495-192">No</span></span>|  
|<span data-ttu-id="64495-193">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="64495-193">**IsSystem**</span></span>|<span data-ttu-id="64495-194">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-194">**int**</span></span>|<span data-ttu-id="64495-195">Indica si el evento ha ocurrido en un proceso del sistema o en un proceso de usuario.</span><span class="sxs-lookup"><span data-stu-id="64495-195">Indicates whether the event occurred on a system process or a user process.</span></span><br /><br /> <span data-ttu-id="64495-196">0 = usuario</span><span class="sxs-lookup"><span data-stu-id="64495-196">0 = user</span></span><br /><br /> <span data-ttu-id="64495-197">1 = sistema</span><span class="sxs-lookup"><span data-stu-id="64495-197">1 = system</span></span>|<span data-ttu-id="64495-198">60</span><span class="sxs-lookup"><span data-stu-id="64495-198">60</span></span>|<span data-ttu-id="64495-199">No</span><span class="sxs-lookup"><span data-stu-id="64495-199">No</span></span>|  
|<span data-ttu-id="64495-200">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="64495-200">**LoginSid**</span></span>|<span data-ttu-id="64495-201">**image**</span><span class="sxs-lookup"><span data-stu-id="64495-201">**image**</span></span>|<span data-ttu-id="64495-202">SID (número de identificación de seguridad) del usuario que ha iniciado la sesión.</span><span class="sxs-lookup"><span data-stu-id="64495-202">The security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="64495-203">Cada SID es único para cada inicio de sesión en el servidor.</span><span class="sxs-lookup"><span data-stu-id="64495-203">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="64495-204">41</span><span class="sxs-lookup"><span data-stu-id="64495-204">41</span></span>|<span data-ttu-id="64495-205">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-205">Yes</span></span>|  
|<span data-ttu-id="64495-206">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="64495-206">**NTDomainName**</span></span>|<span data-ttu-id="64495-207">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64495-207">**nvarchar**</span></span>|<span data-ttu-id="64495-208">Dominio de Windows al que pertenece el usuario.</span><span class="sxs-lookup"><span data-stu-id="64495-208">The Windows domain to which the user belongs.</span></span>|<span data-ttu-id="64495-209">7</span><span class="sxs-lookup"><span data-stu-id="64495-209">7</span></span>|<span data-ttu-id="64495-210">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-210">Yes</span></span>|  
|<span data-ttu-id="64495-211">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="64495-211">**NTUserName**</span></span>|<span data-ttu-id="64495-212">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64495-212">**nvarchar**</span></span>|<span data-ttu-id="64495-213">Nombre del usuario al que pertenece la conexión que generó este evento.</span><span class="sxs-lookup"><span data-stu-id="64495-213">The name of the user that owns the connection that generated this event.</span></span>|<span data-ttu-id="64495-214">6</span><span class="sxs-lookup"><span data-stu-id="64495-214">6</span></span>|<span data-ttu-id="64495-215">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-215">Yes</span></span>|  
|<span data-ttu-id="64495-216">**Prioridad**</span><span class="sxs-lookup"><span data-stu-id="64495-216">**Priority**</span></span>|<span data-ttu-id="64495-217">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-217">**int**</span></span>|<span data-ttu-id="64495-218">Nivel de prioridad de la conversación.</span><span class="sxs-lookup"><span data-stu-id="64495-218">The priority level of the conversation.</span></span>|<span data-ttu-id="64495-219">5</span><span class="sxs-lookup"><span data-stu-id="64495-219">5</span></span>|<span data-ttu-id="64495-220">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-220">Yes</span></span>|  
|<span data-ttu-id="64495-221">**RoleName**</span><span class="sxs-lookup"><span data-stu-id="64495-221">**RoleName**</span></span>|<span data-ttu-id="64495-222">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64495-222">**nvarchar**</span></span>|<span data-ttu-id="64495-223">Rol de la instancia que reconoce el mensaje.</span><span class="sxs-lookup"><span data-stu-id="64495-223">The role of the instance that is acknowledging the message.</span></span> <span data-ttu-id="64495-224">Es **initiator** o **target**.</span><span class="sxs-lookup"><span data-stu-id="64495-224">This is either **initiator** or **target**.</span></span>|<span data-ttu-id="64495-225">38</span><span class="sxs-lookup"><span data-stu-id="64495-225">38</span></span>|<span data-ttu-id="64495-226">No</span><span class="sxs-lookup"><span data-stu-id="64495-226">No</span></span>|  
|<span data-ttu-id="64495-227">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="64495-227">**ServerName**</span></span>|<span data-ttu-id="64495-228">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="64495-228">**nvarchar**</span></span>|<span data-ttu-id="64495-229">Nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cuyo seguimiento se realiza.</span><span class="sxs-lookup"><span data-stu-id="64495-229">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is being traced.</span></span>|<span data-ttu-id="64495-230">26</span><span class="sxs-lookup"><span data-stu-id="64495-230">26</span></span>|<span data-ttu-id="64495-231">No</span><span class="sxs-lookup"><span data-stu-id="64495-231">No</span></span>|  
|<span data-ttu-id="64495-232">**SPID**</span><span class="sxs-lookup"><span data-stu-id="64495-232">**SPID**</span></span>|<span data-ttu-id="64495-233">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-233">**int**</span></span>|<span data-ttu-id="64495-234">Identificador de proceso del servidor que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] asigna al proceso relacionado con el cliente.</span><span class="sxs-lookup"><span data-stu-id="64495-234">The server process ID assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the process that is associated with the client.</span></span>|<span data-ttu-id="64495-235">12</span><span class="sxs-lookup"><span data-stu-id="64495-235">12</span></span>|<span data-ttu-id="64495-236">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-236">Yes</span></span>|  
|<span data-ttu-id="64495-237">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="64495-237">**StartTime**</span></span>|<span data-ttu-id="64495-238">**datetime**</span><span class="sxs-lookup"><span data-stu-id="64495-238">**datetime**</span></span>|<span data-ttu-id="64495-239">Hora a la que se inició el evento, si está disponible.</span><span class="sxs-lookup"><span data-stu-id="64495-239">The time at which the event started, when available.</span></span>|<span data-ttu-id="64495-240">14</span><span class="sxs-lookup"><span data-stu-id="64495-240">14</span></span>|<span data-ttu-id="64495-241">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-241">Yes</span></span>|  
|<span data-ttu-id="64495-242">**StarvationElevation**</span><span class="sxs-lookup"><span data-stu-id="64495-242">**StarvationElevation**</span></span>|<span data-ttu-id="64495-243">**int**</span><span class="sxs-lookup"><span data-stu-id="64495-243">**int**</span></span>|<span data-ttu-id="64495-244">El mensaje se envió con una prioridad más alta que la prioridad configurada para la conversación: 0 = false, 1 = true.</span><span class="sxs-lookup"><span data-stu-id="64495-244">The message was sent with a higher priority than the priority that was configured for the conversation: 0 = false, 1 = true.</span></span>|<span data-ttu-id="64495-245">33</span><span class="sxs-lookup"><span data-stu-id="64495-245">33</span></span>|<span data-ttu-id="64495-246">Sí</span><span class="sxs-lookup"><span data-stu-id="64495-246">Yes</span></span>|  
|<span data-ttu-id="64495-247">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="64495-247">**TransactionID**</span></span>|<span data-ttu-id="64495-248">**bigint**</span><span class="sxs-lookup"><span data-stu-id="64495-248">**bigint**</span></span>|<span data-ttu-id="64495-249">Identificador de la transacción asignado por el sistema.</span><span class="sxs-lookup"><span data-stu-id="64495-249">The system-assigned ID of the transaction.</span></span>|<span data-ttu-id="64495-250">4</span><span class="sxs-lookup"><span data-stu-id="64495-250">4</span></span>|<span data-ttu-id="64495-251">No</span><span class="sxs-lookup"><span data-stu-id="64495-251">No</span></span>|  
  
  