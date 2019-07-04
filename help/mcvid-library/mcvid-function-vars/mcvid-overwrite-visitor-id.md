---
description: Esta propiedad sobrescribe los ID de Experience Cloud y los ID de Analytics del visitante a medida que este navega de un dominio a otro. Para sobrescribir un ID, deberá haber implementado el servicio de ID en cada dominio, así como ser su propietario. Este código no le permite sobrescribir los ID en dominios que no estén bajo su control.
keywords: Servicio de ID
seo-description: Esta propiedad sobrescribe los ID de Experience Cloud y los ID de Analytics del visitante a medida que este navega de un dominio a otro. Para sobrescribir un ID, deberá haber implementado el servicio de ID en cada dominio, así como ser su propietario. Este código no le permite sobrescribir los ID en dominios que no estén bajo su control.
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

Esta propiedad sobrescribe los ID de Experience Cloud y los ID de Analytics del visitante a medida que este navega de un dominio a otro. Para sobrescribir un ID, deberá haber implementado el servicio de ID en cada dominio, así como ser su propietario. Este código no le permite sobrescribir los ID en dominios que no estén bajo su control.

**Sintaxis:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (el valor predeterminado es `false`)

**Ejemplo de código**

Su código JavaScript podría ser similar al del siguiente ejemplo.

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**Casos de uso**

Para hacer un seguimiento de los visitantes del sitio, el servicio de ID escribe un [!DNL Experience Cloud] ID de (o MID) en una cookie de navegador. En la tabla siguiente se enumeran y describen los casos de uso habituales en los que puede interesarle sobrescribir un MID existente que haya definido el servicio de ID en otro dominio.

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso de uso </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar visitantes en diferentes páginas de aterrizaje del dominio</b> </p> </td> 
   <td colname="col2"> <p>Supongamos que es propietario de los dominios A y B. En este caso, puede definir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> cuando: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">cada dominio tenga su propia página de aterrizaje; </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">un visitante tenga ya una cookie (y un MID) definida de una visita anterior al dominio B; </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">quiera identificar de manera coherente a un visitante si llega al dominio B desde el dominio A. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar a visitantes en distintas páginas de aterrizaje y de conversión</b> </p> </td> 
   <td colname="col2"> <p>Supongamos que es propietario de los dominios A y B. En este caso, puede definir <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> cuando: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">el dominio A sea una página de aterrizaje; </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">el dominio B sea una página de conversión, reserva u otra página de fin de flujo de trabajo a parte; </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">un visitante tenga ya definida una cookie (y un MID) de una visita previa al dominio B y sepa que se trata de identificadores MID del lado de cliente menos deseables que identificadores MID del lado de servidor; </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">quiera identificar de manera coherente a un visitante si llega al dominio B desde el dominio A. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Identificar a visitantes desde aplicaciones móviles a navegadores web</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso es ligeramente diferente. Conlleva identificar a los usuarios cuando pasan de una aplicación móvil a su sitio web. En este caso, su visitante ya tiene un MID definido localmente mediante una aplicación móvil y tiene otro MID definido por una cookie en el sitio web. Puede establecer <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span> para sobrescribir el MID definido en la cookie del navegador con el MID definido por la aplicación móvil. </p> </td> 
  </tr> 
 </tbody> 
</table>

