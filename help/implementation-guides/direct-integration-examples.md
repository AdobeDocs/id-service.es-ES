---
description: Estos ejemplos tratan 2 casos de uso comunes relacionados con una integración directa y el ECID. El MID es un ID único y persistente para los visitantes del sitio.
keywords: Servicio de ID de visitante
title: Casos de uso de integraciones directas
exl-id: f2a55b90-8307-4242-b20a-6a3c367a251b
TQID: https://experienceleague.adobe.com/1vfYQsSZiqM3SrnP0lmSrZEWpAMsbwVK8sR0MNitetQ
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 456
ht-degree: 50%

---

# Casos de uso de integraciones directas {#direct-integration-use-cases}

Estos ejemplos tratan 2 casos de uso comunes relacionados con una integración directa y el ECID (también denominado MID). Esta ID es una ID única y persistente para los visitantes del sitio.

>[!TIP]
>
>* Revise y comprenda la [sintaxis de código y las variables](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) de antes de profundizar en los casos de uso.
>* Para obtener más información sobre MID, consulte [Cookies y el servicio de ID de visitante](../introduction/cookies.md).
>

## Caso de uso 1: Tengo un ECID, pero quiero transferir mis ID de visitante y establecer un estado de autenticación {#section-a67d89a343754d1286d03cf08d34b806}

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
   <td colname="col2"> <p>Este caso de uso supone lo siguiente: </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Se tiene un MID para el visitante del sitio. Llamemos a esto ID 1234. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Conozca a este visitante por su propio ID único. Llamemos a esto ID 9876. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Desea vincular el MID (1234) a su propio ID único (9876). </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(Opcional)</i> Quiere establecer un estado de autenticación en este visitante. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Acciones</b> </p> </td> 
   <td colname="col2"> <p>Dadas estas condiciones, realice una llamada al servicio de ID de visitante que incluya lo siguiente: </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">El MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">Su ID de proveedor de datos. Se trata de un ID único asignado a su compañía. Llamemos a esto ID 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">Su ID de visitante (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Opcional)</i> Un ID de estado para definir el estado de autenticación de este visitante. </li> 
    </ul> <p>Y, si ocurre que tiene alguno de los otros parámetros enumerados en la guía de integración directa de <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"></a> (por ejemplo,<span class="codeph"> d_blob</span> o <span class="codeph"> dcs_region</span>, etc.) está bien que pasen esos también. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ejemplo de solución y código</b> </p> </td> 
   <td colname="col2"> <p>Dé este formato a la llamada al servicio de ID de visitante: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Observe cómo la llamada de ejemplo contiene el: </p> 
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
   <td colname="col2"> <p>Este caso de uso supone lo siguiente: </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">No tiene un MID para el visitante del sitio. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Necesita solicitar un MID desde el servicio de ID de visitante. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Conozca su <a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local"> ID de organización de IMS</a>. Llamemos a esto 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Acciones</b> </p> </td> 
   <td colname="col2"> <p>Dadas estas condiciones, realice una llamada al servicio de ID de visitante que incluya su ID de organización de IMS. </p> <p>Y, si ocurre que tiene alguno de los otros parámetros enumerados en la guía de integración directa de <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"></a> (por ejemplo,<span class="codeph"> d_blob</span> o <span class="codeph"> dcs_region</span>, etc.) está bien que pasen esos también. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Ejemplo de solución y código</b> </p> </td> 
   <td colname="col2"> <p>Dé este formato a la llamada al servicio de ID de visitante: </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Observe cómo la llamada de ejemplo contiene su ID de organización de IMS, <span class="codeph">d_orgid=5555</span>. Devuelve un ECID para este visitante. </p> </td> 
  </tr> 
 </tbody> 
</table>

