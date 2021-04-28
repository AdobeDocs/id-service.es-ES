---
description: Esta propiedad establece el ID del contenedor de origen de datos que desea utilizar para las sincronizaciones de ID.
keywords: Servicio de ID
seo-description: Esta propiedad establece el ID del contenedor de origen de datos que desea utilizar para las sincronizaciones de ID.
seo-title: idSyncContainerID
title: idSyncContainerID
uuid: e35dc48b-1aa1-41e3-91c1-ef1e9d2d8b90
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '336'
ht-degree: 100%

---

# idSyncContainerID {#idsynccontainerid}

Esta propiedad establece el ID del contenedor de origen de datos que desea utilizar para las sincronizaciones de ID.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Ejemplo de sintaxis y código </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local">¿Cuáles son los contenedores y cuándo utilizaría esto?</a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Configuración de los ID de contenedor cuando utiliza DIL y VisitorAPI.js </a> </li> 
</ul>

## Ejemplo de sintaxis y código {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Sintaxis:** ` idSyncContainerID: *`valor de ID de contenedor`*`

**Ejemplo de código:**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## ¿Cuáles son los contenedores y cuándo utilizaría esto? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Contenedores**

Los contenedores son los objetos creados por [!DNL Audience Manager]. Aunque no son accesibles externamente, estos contenedores enumeran todas las fuentes de datos que cumplen lo siguiente:

* Están disponibles para usted, pero no se utilizan, para la sincronización de ID.
* Se están utilizando para sincronizar ID.

Aunque no sea un [!DNL Audience Manager] cliente de, su cuenta tendrá estos contenedores si está intercambiando ID con diferentes fuentes de datos en diferentes páginas de su dominio. Esto se debe a que [!DNL Audience Manager] proporciona la tecnología y la funcionalidad del back-end que permite la sincronización de ID.

**Casos de uso**

En función de su situación, es posible que deba o no añadir esta configuración a su código de servicio de ID.

<table id="table_48621F343C7F4760A75F6BCC2DB2DA20"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Condición </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>No se necesita</b> </p> </td> 
   <td colname="col2"> <p>No es necesario utilizar esta configuración en los casos siguientes: </p> <p> 
     <ul id="ul_4D6F794CD65C43D0BEFBA6F5DE420C2E"> 
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">Utiliza el servicio de ID con cualquier solución de <span class="keyword">Experience Cloud</span> ni realiza sincronizaciones de ID con otras fuentes de datos. En este caso, su cuenta tiene un contenedor predeterminado con ID 0 y no se requiere ninguna acción. </li> 
      <li id="li_5657D64D9406407D9B4DB7D8BE4F8EE4">Todas las fuentes de datos están en un solo contenedor. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Necesario</b> </p> </td> 
   <td colname="col2"> <p>Debe utilizar esta configuración cuando se apliquen todas estas condiciones: </p> <p> 
     <ul id="ul_9AFD14FC5A2745F7BD7BE7B64545DA62"> 
      <li id="li_04F0EFBBD71B43608CAAA7E7409D33FE">No utiliza <span class="keyword">Audience Manager </span>. </li> 
      <li id="li_4BFA6DC76CE9455EBBC337FD2FE820BF">Debe sincronizar los ID con otras fuentes de datos organizadas por contenedores. </li> 
      <li id="li_731DA5D1CBF244F8BEBE57C0E2EBA713">Debe sincronizar los ID con fuentes de datos en contenedores diferentes en páginas diferentes de su dominio. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuración de los ID de contenedor cuando utiliza DIL y VisitorAPI.js {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Si ha implementado [!UICONTROL DIL ]* y* VisitorAPI.js en la misma página:

* El código de servicio de ID de visitante tiene prioridad sobre los DIL en las sincronizaciones de ID.
* Establezca solo la `idSyncContainerID` configuración de en el código de servicio de ID.
