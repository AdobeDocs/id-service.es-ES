---
description: Estos ejemplos tratan sobre dos casos de uso habituales relacionados con una integración directa y el Experience Cloud ID (MID). El MID es un ID constante y único para sus visitantes de sitio.
keywords: Servicio de ID
seo-description: Estos ejemplos tratan sobre dos casos de uso habituales relacionados con una integración directa y el Experience Cloud ID (MID). El MID es un ID constante y único para sus visitantes de sitio.
seo-title: Casos de uso de integraciones directas
title: Casos de uso de integraciones directas
uuid: 6de1eb8b-4783-4545-8a64-ab6b9ef93432
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Casos de uso de integraciones directas {#direct-integration-use-cases}

Estos ejemplos tratan sobre dos casos de uso habituales relacionados con una integración directa y el Experience Cloud ID (MID). El MID es un ID constante y único para sus visitantes de sitio.

>[!TIP]
>
>* Revise y comprenda la [sintaxis de código y las variables](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) de antes de profundizar en los casos de uso.
>* Para obtener más información sobre MID, consulte [Cookies y el servicio de identidad de Experience Cloud](../introduction/cookies.md).
>



## Caso de uso 1: Tengo un MID del servicio de identidad de Experience Cloud, pero quiero transferir mis propios ID de visitante y establecer un estado de autenticación {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento de caso de uso </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condiciones</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso presupone que: </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Tiene un MID para el visitante del sitio. Lo llamaremos ID 1234. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Conoce a este visitante por su propio ID único. Lo llamaremos ID 9876. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Quiere vincular el MID (1234) a su propio ID único (9876). </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(Opcional)</i> Quiere establecer un estado de autenticación en este visitante. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Acciones</b> </p> </td> 
   <td colname="col2"> <p>Dadas estas condiciones, realice una llamada al servicio de ID que incluya: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">El MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">Su ID de proveedor de datos. Este es un ID único asignado a su empresa. Lo llamaremos ID 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">Su ID para el visitante (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Opcional)</i> Un ID de estado para definir el estado de autenticación de este visitante. </li> 
    </ul> <p>Y, si ocurre que tiene cualquiera de los otros parámetros enumerados en la <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> guía de integración directa</a> (por ejemplo,<span class="codeph"> d_blob</span> o <span class="codeph">dcs_region</span>, etc.) también es correcto transferirlos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solución y ejemplo de código</b> </p> </td> 
   <td colname="col2"> <p>Dé el siguiente formato a su llamada al servicio de ID: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Observe cómo la llamada de ejemplo contiene el: </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">MID: <span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">MID unido a su ID único para el visitante: <span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">ID de estado de autenticación: <span class="codeph">...d_cid=4444%019876%011</span> (sugerencia: es el último dígito). </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Caso de uso 2: No tengo un MID y necesito generarlo {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elemento de caso de uso </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Condiciones</b> </p> </td> 
   <td colname="col2"> <p>Este caso de uso presupone que: </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">No tiene un MID para el visitante del sitio. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Debe solicitar un MID al servicio de ID. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Conoce su <a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">ID de organización</a>. Lo llamaremos 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Acciones</b> </p> </td> 
   <td colname="col2"> <p>Dadas estas condiciones, realice una llamada al servicio de ID que incluya su ID de organización. </p> <p>Y, si ocurre que tiene cualquiera de los otros parámetros enumerados en la <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> guía de integración directa</a> (por ejemplo,<span class="codeph"> d_blob</span> o <span class="codeph">dcs_region</span>, etc.) también es correcto transferirlos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solución y ejemplo de código</b> </p> </td> 
   <td colname="col2"> <p>Dé el siguiente formato a su llamada al servicio de ID: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Observe cómo la llamada de ejemplo contiene su ID de organización, <span class="codeph">d_orgid=5555</span>. Devolvería un Experience Cloud ID<span class="keyword"></span> para este visitante. </p> </td> 
  </tr> 
 </tbody> 
</table>

