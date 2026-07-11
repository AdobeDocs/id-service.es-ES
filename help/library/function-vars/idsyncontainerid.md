---
description: Esta propiedad establece el ID del contenedor de origen de datos que desea utilizar para las sincronizaciones de ID.
keywords: Servicio de ID de visitante
title: idSyncContainerID
exl-id: 6c4cd41b-902b-4872-8c3f-475a834b76f4
TQID: https://experienceleague.adobe.com/bDW5Z4LKbLW2igmRsJ-QxajnBj8KyvoTypUjUekElj4
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 328
ht-degree: 60%

---

# idSyncContainerID{#idsynccontainerid}

Esta propiedad establece el ID del contenedor de origen de datos que desea utilizar para las sincronizaciones de ID.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-b0c50732b1c84bed8616e82e8e83d58c" format="dita" scope="local"> Ejemplo de sintaxis y código </a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-6aed44fbe9d6401a8f912cb0d98339a7" format="dita" scope="local">¿Cuáles son los contenedores y cuándo utilizaría esto?</a> </li> 
 <li> <a href="../../library/function-vars/idsyncontainerid.md#section-f283cb69c8de4348b5316cc4e02a3e9e" format="dita" scope="local"> Configuración de los ID de contenedor cuando utiliza DIL y VisitorAPI.js </a> </li> 
</ul>

## Ejemplo de sintaxis y código {#section-b0c50732b1c84bed8616e82e8e83d58c}

**Sintaxis:** `idSyncContainerID: *`valor de ID de contenedor`*`

**Ejemplo de código:**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Set container ID 
   idSyncContainerID:80 
});
```

## ¿Cuáles son los contenedores y cuándo utilizaría esto? {#section-6aed44fbe9d6401a8f912cb0d98339a7}

**Contenedores**

Los contenedores son objetos creados por Audience Manager. Aunque no son accesibles externamente, estos contenedores enumeran todas las fuentes de datos que cumplen lo siguiente:

* Están disponibles para usted, pero no se utilizan, para la sincronización de ID.
* Se están utilizando para sincronizar ID.

Aunque no sea cliente de Audience Manager, su cuenta tendrá estos contenedores si está intercambiando ID con diferentes fuentes de datos en diferentes páginas de su dominio. Esto se debe a que Audience Manager proporciona la tecnología y la funcionalidad del back-end que permite la sincronización de ID.

**Casos de uso**

En función de su situación, es posible que deba o no añadir esta configuración a su código de servicio de ID de visitante.

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
      <li id="li_0F048A6AC7BE4450AFA1B20B1AC25808">Utiliza el servicio de ID de visitante con cualquier solución de CX Enterprise y no realiza sincronizaciones de ID con otras fuentes de datos. En este caso, su cuenta tiene un contenedor predeterminado con ID 0 y no se requiere ninguna acción. </li> 
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

## Estableciendo identificadores de contenedor cuando usa DIL y `VisitorAPI.js` {#section-f283cb69c8de4348b5316cc4e02a3e9e}

Si ha implementado [!UICONTROL DIL] *y* `VisitorAPI.js` en la misma página:

* El código del servicio de ID de visitante tiene prioridad sobre DIL en las sincronizaciones de ID.
* Establezca solo la configuración de `idSyncContainerID` en el código del servicio de ID de visitante.

