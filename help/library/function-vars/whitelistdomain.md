---
description: Estas configuraciones permiten a diferentes instancias del código de servicio de ID implementadas en un iFrame y en la página principal comunicarse las unas con las otras. Están diseñadas para ayudar a resolver problemas con 2 casos de uso específicos en los que puede que sea posible, o no, controlar la página o el dominio principal y en los que tenga el código de servicio de ID cargando en el iFrame de un dominio que controla. Estas están disponibles en la versión 2.2 del código de VisitorAPI.js y en las posteriores.
keywords: Servicio de ID
seo-description: Estas configuraciones permiten a diferentes instancias del código de servicio de ID implementadas en un iFrame y en la página principal comunicarse las unas con las otras. Están diseñadas para ayudar a resolver problemas con 2 casos de uso específicos en los que puede que sea posible, o no, controlar la página o el dominio principal y en los que tenga el código de servicio de ID cargando en el iFrame de un dominio que controla. Estas están disponibles en la versión 2.2 del código de VisitorAPI.js y en las posteriores.
seo-title: whitelistParentDomain y whitelistIframeDomains
title: whitelistParentDomain y whitelistIframeDomains
uuid: 6b66a4d0-fea2-4d98-963e-0c4f4ab1efb6
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# whitelistParentDomain y whitelistIframeDomains{#whitelistparentdomain-and-whitelistiframedomains}

Estas configuraciones permiten a diferentes instancias del código de servicio de ID implementadas en un iFrame y en la página principal comunicarse las unas con las otras. Están diseñadas para ayudar a resolver problemas con 2 casos de uso específicos en los que puede que sea posible, o no, controlar la página o el dominio principal y en los que tenga el código de servicio de ID cargando en el iFrame de un dominio que controla. Estas están disponibles en la versión 2.2 del código de VisitorAPI.js y en las posteriores.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-f645198bbaba4fba8961acb6e88d1470" format="dita" scope="local"> Sintaxis </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-09d0049fe88a473baa69d404c50bf8ae" format="dita" scope="local"> Ejemplo de código </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-fc2eeb93546b406fae3b102dbcd11de7" format="dita" scope="local"> Casos de uso </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2" format="dita" scope="local"> Protección y seguridad de configuración </a> </li> 
 <li> <a href="../../library/function-vars/whitelistdomain.md#section-30c6a9f4dcdc4265a1149260b97cc057" format="dita" scope="local"> Métodos de API de visitante compatibles </a> </li> 
</ul>

## Sintaxis {#section-f645198bbaba4fba8961acb6e88d1470}

Se utilizan los dos elementos de configuración cuando utiliza este código.

<table id="table_237108A4D40F4AAC981D0060BA68F881"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Sintaxis de configuración </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistParentDomain: " <span class="varname"> Nombre del dominio de la página principal </span>" </span> </p> </td> 
   <td colname="col2"> <p>Acepta un nombre de dominio transferido como una cadena. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> whitelistIframeDomains: [ <span class="varname"> "Dominio de iFrame","Dominio de iFrame","Dominio de iFrame" </span>] </span> </p> </td> 
   <td colname="col2"> <p>Acepta uno o más nombres de dominio de iFrame transferidos como una matriz. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Ejemplo de código {#section-09d0049fe88a473baa69d404c50bf8ae}

Su código de [!UICONTROL servicio de ID] configurado puede tener un aspecto similar al de este ejemplo.

```js
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
 ... 
 //Add parent page domain name and iFrame domain names 
 whitelistParentDomain: "parentpageA.com", 
 whitelistIframeDomains: ["iFrameDomain1.com","iFrameDomain2.com"], 
 ... 
 } 
);
```

## Casos de uso {#section-fc2eeb93546b406fae3b102dbcd11de7}

Estas configuraciones ayudan a resolver el problema de establecer una cookie de servicio de ID y asignar un ID de visitante cuando los navegadores bloquean cookies de terceros, y si se aplican una de estas condiciones:

* Controla o no controla la página/dominio principal.
* El código de servicio de ID no está instalado en la página principal, sino que está implementado en un iFrame.

>[!TIP]
>
>También es posible que desee implementar estas configuraciones cuando vaya a ofrecer vídeo en un iFrame con [Video Heartbeat](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/). Video Heartbeat necesita un servicio de ID (el MID) para funcionar correctamente.

**Caso de uso 1: El navegador bloquea cookies de terceros y el servicio de ID se implementa en el iFrame y la página principal**

<table id="table_B479AA96DBE64685A253A6DF98D81B31"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento de caso de uso </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condiciones</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso incluye las condiciones siguientes: </p> <p> 
     <ul id="ul_DC748846585745B0AB74398D82BDA53A"> 
      <li id="li_6E04CF0B6A204B4D8856656B0C9EF2A5">La empresa A implementa el servicio de ID en su página de inicio. </li> 
      <li id="li_B53AE0F0C69844E7B6C4D3464C57883B">La empresa A implementa el servicio de ID en iFrame en su página de inicio. </li> 
      <li id="li_07E0A6D7BEB140E4B9FB6C7B9629B860">La empresa A es propietaria de la página principal y el iFrame ha implementado el servicio de ID en ambos lados. </li> 
      <li id="li_76967BD69DDB40A8A9C915DADC58AC62">Un cliente carga la página principal en un navegador que bloquea cookies de terceros. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Resultados</b> </p> </td> 
   <td colname="col2"> <p>Dadas estas condiciones, el servicio de ID: </p> <p> 
     <ul id="ul_12356701501E40DFA57903494FFE58F7"> 
      <li id="li_B57EDF1B0762486F95FA6526C047390C">Funciona correctamente en la página principal. Solicita y establece la cookie AMCV y asigna un ID único al visitante del sitio. </li> 
      <li id="li_BA9F42C759E747EAAE14DD3FBB6130A5">No funciona en el iFrame. Esto se debe a que el navegador ve el iFrame como un dominio de terceros e impide que el servicio de ID establezca la cookie AMCV. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solución</b> </p> </td> 
   <td colname="col2"> <p>Modifique la función <span class="codeph">Visitor.getInstance</span> del servicio de ID en el iFrame con estas configuraciones de listas de elementos permitidos. Especifique los dominios principal y secundario en el código. Estas configuraciones permiten al código de servicio de ID del iFrame comprobar el código de servicio de ID en la página principal para un ID de visitante. </p> <p>Si el código de servicio de ID en el iFrame no recibe una página principal de respuesta, estas configuraciones generan un ID de visitante local. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Caso de uso 2: Solicitar un ID de un iFrame integrado en una página principal que usted no controla o que no utiliza el servicio de ID**

<table id="table_1F21710F9D5F493BA6BA5974F2966DF4"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento de caso de uso </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condiciones</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso incluye las condiciones siguientes: </p> <p> 
     <ul id="ul_356E8FB0B1D14F46A844FE5281967E28"> 
      <li id="li_1285D945361842268B46FB492A3B5AA5">La empresa A no utiliza el servicio de ID. </li> 
      <li id="li_880D6D473F8342FF9BB49FCE111FD61A">La empresa A carga un iFrame en la página. Este iFrame pertenece a la empresa B y se carga en un dominio aparte que no pertenece a la empresa A. </li> 
      <li id="li_7988F0272B094FE0B398006AD4E6F81B">El navegador bloquea las cookies de terceros. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Resultados</b> </p> </td> 
   <td colname="col2"> <p>Dadas estas condiciones, el servicio de ID: </p> <p> 
     <ul id="ul_A92D90896E5A42C5804AC5CE83E8EB25"> 
      <li id="li_9734EA9C5D9D4F908DE783188C9E5530">No funciona en el iFrame. Esto se debe a que el navegador ve el iFrame como un dominio de terceros e impide que el servicio de ID establezca la cookie AMCV. </li> 
      <li id="li_3F4BE9048E774902A867D67E5A80674D">No puede obtener un ID de visitante de la página principal porque la empresa A no utiliza este servicio. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solución</b> </p> </td> 
   <td colname="col2"> <p>Modifique la función <span class="codeph">Visitor.getInstance</span> del servicio de ID en el iFrame con estas configuraciones de listas de elementos permitidos. Especifique los dominios principal y secundario en el código. Estas configuraciones permiten al código de servicio de ID del iFrame comprobar el código de servicio de ID en la página principal para un ID de visitante. </p> <p>Si el código de servicio de ID en el iFrame no recibe una página principal de respuesta, estas configuraciones generan un ID de visitante local. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Protección y seguridad de configuración {#section-2b1ce31fab034e1ca0f6b1c3cc57a6e2}

Puede implementar estas configuraciones de forma segura porque:

* El servicio de ID implementado en el dominio principal y el dominio de iFrame deben utilizar el mismo ID de organización. Estas configuraciones de lista de elementos permitidos no funcionarán cuando los ID de organización de la página principal o del iFrame son diferentes.
* Estas configuraciones solo se comunican con el dominio y los iFrames especificados en el código.
* La comunicación entre el iFrame y la página principal sigue un formato específico. Si el servicio de ID de la página principal no recibe una solicitud en el formato previsto, no se podrá realizar este proceso de uso compartido.

## Métodos de API de visitante compatibles {#section-30c6a9f4dcdc4265a1149260b97cc057}

El servicio de ID admite un conjunto limitado de métodos API públicos cuando implementa estas configuraciones de listas de elementos permitidos. Los métodos admitidos varían en función de los escenarios de casos de uso descritos anteriormente.

<table id="table_0FF9E529FD1C43A8A3B2B0D789C8E83C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso de uso </th> 
   <th colname="col2" class="entry"> Métodos compatibles </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Caso 1</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_99FAC8608F4C4B39805EEAA6297DB771"> 
      <li id="li_B13F6C4119F44F17963794B1E2046B1F"> <span class="codeph"> getMarketingCloudID </span> </li> 
      <li id="li_9C1B5C00A17F467CAB7EFE5F0D040777"> <span class="codeph"> getAudienceManagerLocationHint </span> </li> 
      <li id="li_30D4608F4C3849659FCBA97D88A10F0C"> <span class="codeph"> getAudienceManagerBlob </span> </li> 
      <li id="li_BA359596C80147EEA89CABCE83F123CA"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_26774089B6854CD6A3216043B6EEA01B"> <span class="codeph"> getCustomerIDs </span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Caso 2</b> </p> </td> 
   <td colname="col2"> <p> 
     <ul id="ul_CCAD7E362E7F4DAB9D5C3E166EEE6BDD"> 
      <li id="li_1F0B006BAD044ECBA5604625DE411E84"> <span class="codeph"> getSupplementalDataID </span> </li> 
      <li id="li_C6022223C8314B9C923202207C7472EA"> <span class="codeph"> getMarketingCloudVisitorID </span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

