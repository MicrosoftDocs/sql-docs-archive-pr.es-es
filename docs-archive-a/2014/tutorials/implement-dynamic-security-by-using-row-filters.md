---
title: Implementar la seguridad dinámica mediante filtros de fila | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8bf03c45-caf5-4eda-9314-e4f8f24a159f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 09a15f818f57d7a9d808c89ced41b285536a7883
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/04/2020
ms.locfileid: "87663238"
---
# <a name="implement-dynamic-security-by-using-row-filters"></a>Implementar seguridad dinámica utilizando filtros de filas
  En esta lección complementaria, creará un rol adicional que implemente seguridad dinámica. La seguridad dinámica proporciona seguridad de nivel de fila en función del identificador de inicio de sesión o del nombre de usuario de la persona que tenga la sesión iniciada. Para obtener más información, consulte [Roles &#40;SSAS tabular&#41;](https://docs.microsoft.com/analysis-services/tabular-models/roles-ssas-tabular).  
  
 Para implementar la seguridad dinámica, debe agregar una tabla al modelo que contiene los nombres de usuario de Windows de los usuarios que pueden crear una conexión al modelo como un origen de datos y examinar los objetos y datos del modelo. El modelo que se crea con este tutorial está en el contexto de Adventure Works Corp.; sin embargo, para completar esta lección, debe agregar una tabla que contenga usuarios de su propio dominio. No necesitará contraseñas para los nombres de usuario que se van a agregar. Para crear una tabla de seguridad de empleados, con una pequeña muestra de usuarios de su propio dominio, utilizará la función de pegar para pegar datos de empleados de una hoja de cálculo de Excel. En un escenario real, la tabla que contiene los nombres de usuario que agrega a un modelo utilizaría normalmente una tabla de una base de datos real como origen de datos; por ejemplo, una tabla dimEmployee real.  
  
 Para implementar la seguridad dinámica, usará dos nuevas funciones de DAX: función de [nombre de usuario &#40;&#41;Dax](/dax/username-function-dax) y [función VALORBUSCAR &#40;&#41;Dax ](/dax/lookupvalue-function-dax). Estas funciones, aplicadas en una fórmula de filtro de fila, se definen en un nuevo rol. Con la función LOOKUPVALUE, la fórmula especifica un valor de la tabla Employee Security y pasa ese valor a la función USERNAME, que especifica el nombre del usuario que ha iniciado sesión como perteneciente a este rol. El usuario puede examinar solo los datos especificados por los filtros de fila del rol. En este escenario, especificará que los empleados de ventas solo podrán examinar los datos de ventas por Internet de los territorios de ventas de los que son miembros.  
  
 Para completar esta lección complementaria, realizará una serie de tareas. Las tareas que solo se realizan en este escenario de modelo tabular de Adventure Works, pero no que se aplicarían necesariamente a un escenario real, se identifican como tales. Cada tarea incluye información adicional que describe el propósito de la tarea.  
  
 Tiempo estimado para completar esta lección: **30 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
 Este tema de la lección complementaria forma parte de un tutorial de modelado tabular, que debe completar en orden. Antes de realizar las tareas de esta lección complementaria, debe haber completado todas las lecciones anteriores.  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>Agregar la tabla dimSalesTerritory al proyecto de modelo tabular AW Internet Sales  
 Para implementar la seguridad dinámica en este escenario de ejemplo Adventure Works, debe agregar dos tablas adicionales al modelo. La primera tabla que agregará es dimSalesTerritory (como Sales Territory) procedente de la misma base de datos AdventureWorksDW. Aplicará posteriormente un filtro de fila a la tabla Sales Territory que define los datos concretos que el usuario que ha iniciado sesión puede examinar.  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>Para agregar la tabla dimSalesTerritory  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y, a continuación, en **Conexiones existentes**.  
  
2.  En el cuadro de diálogo **Conexiones existentes** , compruebe que esté seleccionada la conexión al origen de datos **BD de Adventure Works de SQL** y haga clic en **Abrir**.  
  
     Si aparece el cuadro de diálogo Credenciales de suplantación, escriba las credenciales de suplantación que usó en la lección 2 sobre incorporación de datos.  
  
3.  En la página **Elegir cómo importar los datos** , deje seleccionada la opción **Seleccionar en una lista de tablas y vistas para elegir los datos a importar** y haga clic en **Siguiente**.  
  
4.  En la página **Seleccionar tablas y vistas** , seleccione la tabla **DimSalesTerritory** .  
  
5.  En la columna Nombre descriptivo, escriba **Sales Territory**.  
  
6.  Haga clic en **Vista previa y filtro**.  
  
7.  Anule la selección de la columna **SalesTerritoryAlternateKey** y haga clic en **Aceptar**.  
  
8.  En la página **Seleccionar tablas y vistas** , haga clic en **Finalizar**.  
  
     Las nueva tabla se agregarán al final del área de trabajo del modelo. Los objetos y datos de la tabla de origen dimSalesTerritory se importan a la nueva tabla Sales Territory del modelo tabular AW Internet Sales.  
  
9. Una vez importada la tabla, haga clic en **Cerrar**.  
  
## <a name="give-the-columns-friendly-names"></a>Proporcionar nombres descriptivos a las columnas  
 En esta tarea, cambiará el nombre de las columnas de la tabla Sales Territory para darles un nombre descriptivo. No siempre es necesario proporcionar nombres descriptivos de tablas y/o columnas; sin embargo, facilita la navegación de su proyecto de modelo por el diseñador de modelos y los usuarios pueden explorar más fácilmente los objetos y los datos del modelo en una lista de campos de la aplicación cliente.  
  
#### <a name="to-rename-columns-in-the-sales-territory-table"></a>Para cambiar el nombre de las columnas de la tabla Sales Territory  
  
-   En el diseñador de modelos, cambie el nombre a las columnas de la tabla **Sales Territory** :  
  
     **Sales Territory**  
  
    |Nombre de origen|Nombre descriptivo|  
    |-----------------|-------------------|  
    |SalesTerritoryKey|Sales Territory Id|  
    |SalesTerritoryRegion|Región del territorio de ventas|  
    |SalesTerritoryCountry|País del territorio de ventas|  
    |SalesTerritoryGroup|Grupo de territorios de ventas|  
  
## <a name="add-a-table-with-user-name-data"></a>Incorporación de una tabla con datos de nombres de usuario  
 Puesto que la tabla dimEmployee de la base de datos de ejemplo AdventureWorksDW contiene usuarios del dominio AdventureWorks, y esos nombres de usuario no existen en su propio entorno, debe crear una tabla en el modelo que contenga una pequeña muestra (tres) de usuarios reales de su organización. Agregará después estos usuarios al nuevo rol como miembros. No necesita las contraseñas de los nombres de usuario de ejemplo, pero necesitará nombres de usuario de Windows reales de su propio dominio.  
  
#### <a name="to-add-an-employee-security-table"></a>Para agregar una tabla de seguridad de empleados  
  
1.  Abra Microsoft Excel para crear una hoja de cálculo.  
  
2.  Copie la siguiente tabla, incluida la fila de encabezado y, luego, péguela en la hoja de cálculo.  
  
    |Employee Id|Sales Territory Id|Nombre|Apellido|Login Id|  
    |-----------------|------------------------|----------------|---------------|--------------|  
    |1|2|\<user first name>|\<user last name>|\<domain\username>|  
    |1|3|\<user first name>|\<user last name>|\<domain\username>|  
    |2|4|\<user first name>|\<user last name>|\<domain\username>|  
    |3|5|\<user first name>|\<user last name>|\<domain\username>|  
  
3.  En la nueva hoja de cálculo, reemplace el nombre, el apellido, y el dominio\nombreUsuario con los nombres y los id. de inicio de sesión de tres usuarios de su organización. Coloque el mismo usuario en las dos primeras filas, para el Employee Id 1. Esto mostrará que este usuario pertenece a más de un territorio de ventas. Deje los campos Employee Id y Sales Territory Id como están.  
  
4.  Guarde la hoja de cálculo como `Sample Employee` .  
  
5.  En la hoja de cálculo, seleccione todas las celdas con datos de empleados, incluidos los encabezados, haga clic con el botón derecho en los datos seleccionados y, después, haga clic en **Copiar**.  
  
6.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Edición** y, después, en **Pegar**.  
  
     Si la opción Pegar aparece deshabilitada, haga clic en cualquier columna de una tabla de la ventana del diseñador de modelos, haga clic en el menú **Edición** y, después, haga clic en **Pegar**.  
  
7.  En el cuadro de diálogo **vista previa de pegado** , en **nombre de tabla**, escriba `Employee Security` .  
  
8.  En **Datos que se van a pegar**, compruebe que los datos incluyen todos los datos y encabezados de usuario de la hoja de cálculo Empleado de ejemplo.  
  
9. Compruebe que la casilla **Usar primera fila como encabezados de columna** está activada y, luego, haga clic en **Aceptar**.  
  
     Se crea una nueva tabla denominada Employee Security con los datos de empleado copiados de la hoja de cálculo Empleado de ejemplo.  
  
## <a name="create-relationships-between-internet-sales-geography-and-sales-territory-table"></a>Crear relaciones entre las tablas Internet Sales, Geography y Sales Territory  
 Todas las tablas Internet sales, Geography y territorio de ventas contienen una columna común, ID. de territorio de ventas. La columna ID. de territorio de ventas de la tabla territorio de ventas contiene valores con un identificador diferente para cada territorio de ventas.  
  
#### <a name="to-create-relationships-between-the-internet-sales-geography-and-the-sales-territory-table"></a>Para crear relaciones entre las tablas Internet Sales, Geography y Sales Territory  
  
1.  En el diseñador de modelos, en la vista de diagrama, en la tabla **Geography** , haga clic en la columna **Sales Territory Id** y manténgala seleccionada, arrastre el cursor hasta la columna **Sales Territory Id** de la tabla **Sales Territory** y suéltelo.  
  
2.  En la tabla **Internet Sales** , haga clic en la columna **Sales Territory Id** y manténgala seleccionada, arrastre el cursor hasta la columna **Sales Territory Id** de la tabla **Sales Territory** y suéltelo.  
  
     Observe que la propiedad Active de esta relación es False, lo que significa que está inactiva. Esto se debe a que la tabla Internet Sales tiene ya otra relación activa que se utiliza en las medidas.  
  
## <a name="hide-the-employee-security-table-from-client-applications"></a>Ocultar la tabla Employee Security en las aplicaciones cliente  
 En esta tarea, ocultará la tabla Employee Security y la dejará de aparecer en la lista de campos de una aplicación cliente. Tenga en cuenta que ocultar una tabla no significa protegerla. Los usuarios podrán seguir consultando los datos de la tabla Employee Security si saben cómo hacerlo. Para proteger los datos de la tabla Employee Security e impedir que los usuarios puedan consultar sus datos, aplicará un filtro en una tarea posterior.  
  
#### <a name="to-hide-the-employee-table-from-client-applications"></a>Para ocultar la tabla Employee Security en las aplicaciones cliente  
  
-   En el Diseñador de modelos, en la vista de diagrama, haga clic con el botón derecho en el encabezado de tabla **Empleado** y, luego, haga clic en **Ocultar en herramientas cliente**.  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Creación de un rol de usuario Empleados de ventas por territorio  
 En esta tarea, creará un rol de usuario. Este rol incluirá un filtro de fila que define qué filas de la tabla Sales Territory estarán visibles para los usuarios. El filtro se aplicará en una dirección de relación de uno-a muchos para el resto de las tablas relacionadas con Sales Territory. También aplicará un filtro sencillo que proteja la tabla Seguridad de los empleados de las consultas por parte de cualquier usuario que sea miembro del rol.  
  
> [!NOTE]  
>  El rol Empleados de ventas por territorio que creará en esta lección permitirá a los miembros examinar (o consultar) solo los datos de ventas del territorio de ventas al que pertenecen. Si agrega un usuario como miembro al rol de empleados de ventas por territorio que también existe como miembro del rol creado en [Lección 12: Crear roles](../analysis-services/lesson-11-create-roles.md), obtendrá una combinación de permisos. Cuando un usuario es miembro de varios roles, los permisos y filtros de fila definidos para cada rol son acumulativos. Es decir, el usuario tendrá los mayores permisos determinados por la combinación de roles.  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Procedimiento para crear un rol de usuario Empleados de ventas por territorio  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y luego haga clic en **Roles**.  
  
2.  En el cuadro de diálogo **Administrador de roles** , haga clic en **Nuevo**.  
  
     Se agrega a la lista un nuevo rol con el permiso Ninguno.  
  
3.  Haga clic en el nuevo rol y, a continuación, en la columna **nombre** , cambie el nombre del rol a `Sales Employees by Territory` .  
  
4.  En la columna **Permisos**, haga clic en la lista desplegable y, luego, seleccione el permiso **Lectura**.  
  
5.  Haga clic en la pestaña **Miembros** y luego en **Agregar**.  
  
6.  En el cuadro de diálogo **Seleccionar usuario o grupo** , en **Escribir los nombres de objeto para seleccionar**, escriba el primer nombre de usuario de ejemplo que ha usado al crear la tabla Employee Security. Haga clic en **Comprobar nombres** para comprobar que el nombre de usuario es válido y, luego, haga clic en **Aceptar**.  
  
     Repita este paso, agregando los otros nombres de usuario de ejemplo que utilizó al crear la tabla Employee Security.  
  
7.  Haga clic en la pestaña **Filtros de fila** .  
  
8.  En la `Employee Security` tabla, en la columna **filtro Dax** , escriba la siguiente fórmula.  
  
     `=FALSE()`  
  
     Cuando termine de crear la fórmula, presione ENTRAR.  
  
     Esta fórmula especifica que todas las columnas se resolverán según la condición booleana false; por lo tanto, ningún miembro del rol de usuario de empleados de ventas por territorio podrá consultar las columnas de la tabla Employee Security.  
  
9. Para la tabla **Sales Territory** , escriba la siguiente fórmula.  
  
     `='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 'Employee Security'[Login Id], USERNAME(), 'Employee Security'[Sales Territory Id], 'Sales Territory'[Sales Territory Id])`  
  
     Cuando termine de crear la fórmula, presione ENTRAR.  
  
     En esta fórmula, la función LOOKUPVALUE devuelve todos los valores de la columna Employee Security[Sales Territory Id], donde Employee Security[Login Id] coincide con el nombre de usuario actual que ha iniciado sesión en Windows y Employee Security[Sales Territory Id] coincide con Sales Territory[Sales Territory Id].  
  
     A continuación, se utiliza el conjunto de identificadores del territorio de ventas devueltos por LOOKUPVALUE para limitar las filas que se muestran en la tabla de territorio de ventas. Solo se mostrarán las filas donde el Id. de territorio de ventas de la fila sea el conjunto de identificadores devueltos por la función LOOKUPVALUE.  
  
10. En el cuadro de diálogo Administrador de roles, haga clic en **Aceptar**.  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Prueba del rol de usuario Empleados de ventas por territorio  
 En esta tarea, utilizará la característica Analizar en Excel de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] para probar la eficacia de los empleados de ventas por el rol usuario Territorio. Especificará uno de los nombres de usuario que ha agregado a la tabla Employee Security como miembro del rol. Este nombre de usuario se utilizará como el nombre de usuario efectivo en la conexión creada entre Excel y el modelo.  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Procedimiento para probar el rol de usuario Empleados de ventas por territorio  
  
1.  En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y después en **Analizar en Excel**.  
  
2.  En el cuadro de diálogo **Analizar en Excel**, en **Especifique el nombre de usuario o rol que se va a usar al conectarse al modelo**, seleccione **Otro usuario de Windows**. Después, haga clic en **Examinar**.  
  
3.  En el cuadro de diálogo **Seleccionar usuario o grupo** , en **Escriba el nombre del objeto que desea seleccionar**, escriba uno de los nombres de usuario que se incluyeron en la tabla de empleados y luego haga clic en **Comprobar nombres**.  
  
4.  Haga clic en **Aceptar** para cerrar el **Seleccionar usuario o grupo** cuadro de diálogo y, a continuación, haga clic en **Aceptar** para cerrar el **analizar en Excel** cuadro de diálogo.  
  
     Se abrirá Excel con un nuevo libro. Se crea automáticamente una tabla dinámica. La lista de campos de tabla dinámica incluye todos la mayoría de campos de datos disponibles en su nuevo modelo.  
  
     Observe que la tabla Employee Security no está visible en la lista de campos de la tabla dinámica. Esto se debe a que eligió ocultar esta tabla de las herramientas cliente en una tarea anterior.  
  
5.  En la **lista de campos de tabla dinámica** , en **∑ Internet Sales** (medidas), seleccione la medida **Internet Total Sales** . La medida se agregará a los campos **Valores** .  
  
6.  En la **lista de campos de tabla dinámica** , seleccione la columna **Sales Territory Id** de la tabla **Sales Territory** . La columna se agregará a los campos **Etiquetas de fila** .  
  
     Tenga en cuenta que las cifras de ventas por Internet solo aparecen para la región a la que pertenece el nombre de usuario efectivo que usó. Si selecciona otra columna; por ejemplo, City, en la tabla Geography como un campo de etiqueta de fila, solo se mostrarán las ciudades del territorio de ventas al que el usuario efectivo pertenece.  
  
     Este usuario no podrá examinar o consultar los datos de ventas por Internet para otros territorios distintos de aquel al que pertenece, porque el filtro de fila definido para la tabla Sales Territory en el rol de usuario de empleados de ventas por territorio protege eficazmente los datos relacionados con otros territorios de ventas.  
  
## <a name="see-also"></a>Consulte también  
 [Función USERNAME &#40;&#41;DAX](/dax/username-function-dax)   
 [Función VALORBUSCAR &#40;DAX&#41;](/dax/lookupvalue-function-dax)   
 [Función CUSTOMDATA &#40;DAX&#41;](/dax/customdata-function-dax)  
  
  
