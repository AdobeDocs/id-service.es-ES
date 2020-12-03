---
description: Esta propiedad sobrescribe los Experience Cloud ID y los ID de Analytics del visitante a medida que este navega de un dominio a otro. Para sobrescribir un ID, debe ser propietario del servicio de ID y haberlo implementado en cada dominio. Este código no le permite sobrescribir los ID en dominios que no controla.
keywords: ID Service
seo-description: Esta propiedad sobrescribe los Experience Cloud ID y los ID de Analytics del visitante a medida que este navega de un dominio a otro. Para sobrescribir un ID, debe ser propietario del servicio de ID y haberlo implementado en cada dominio. Este código no le permite sobrescribir los ID en dominios que no controla.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 32%

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Esta propiedad sobrescribe los Experience Cloud ID y los ID de Analytics del visitante a medida que este navega de un dominio a otro. Para sobrescribir un ID, debe ser propietario del servicio de ID y haberlo implementado en cada dominio. Este código no le permite sobrescribir los ID en dominios que no controla.

**Sintaxis:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (el valor predeterminado es `false`)

**Ejemplo de código**

El código JavaScript podría tener un aspecto similar al del siguiente ejemplo.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Casos de uso**

Para hacer un seguimiento de los visitantes del sitio, el servicio de ID escribe un [!DNL Experience Cloud] ID de (o MID) en una cookie de navegador. La siguiente tabla lista y describe los casos de uso comunes en los que podría desear sobrescribir un MID existente establecido por el servicio de ID en otro dominio.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso de uso </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar visitantes en diferentes páginas de aterrizaje de dominio</b> </p> </td> 
   <td colname="col2"> <p>Supongamos que es propietario de los dominios A y B. En este caso, puede definir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> cuando: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">Cada dominio tiene su propia página de aterrizaje. </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">Un visitante ya tiene una cookie (y un MID) establecida desde una visita anterior al dominio B. </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">Desea identificar un visitante de forma consistente si llega al dominio B desde el dominio A. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar visitantes en las páginas de aterrizaje y conversión</b> </p> </td> 
   <td colname="col2"> <p>Supongamos que es propietario de los dominios A y B. En este caso, puede definir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> cuando: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">El dominio A es una página de aterrizaje. </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">El dominio B es una página de conversión, reservación u otra página de fin de flujo de trabajo independiente. </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">Un visitante ya tiene una cookie (y un MID) establecida desde una visita anterior al dominio B y sabe que son MID del lado del cliente menos deseables que MID del lado del servidor. </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">Desea identificar un visitante de forma consistente si llega al dominio B desde el dominio A. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identifique los visitantes de las aplicaciones móviles a los navegadores web</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso es ligeramente diferente. Implica identificar a los usuarios a medida que pasan de una aplicación móvil a su sitio web. En este caso, su visitante ya tiene un MID definido localmente por una aplicación móvil y tiene otro MID definido en una cookie de su sitio web. Puede establecer <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> para sobrescribir el MID definido en la cookie del navegador con el MID definido por la aplicación móvil. </p> </td> 
  </tr> 
 </tbody> 
</table>

