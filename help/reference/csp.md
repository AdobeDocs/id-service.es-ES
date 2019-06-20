---
description: Una política de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores control sobre qué tipo de recursos se cargan en una página web. Lea esta sección si utiliza el servicio de ID y tiene CSP estrictas que utilizan listas de elementos permitidos para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe que se enumeran aquí a sus listas de elementos permitidos de CSP.
keywords: Servicio de ID
seo-description: Una política de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores control sobre qué tipo de recursos se cargan en una página web. Lea esta sección si utiliza el servicio de ID y tiene CSP estrictas que utilizan listas de elementos permitidos para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe que se enumeran aquí a sus listas de elementos permitidos de CSP.
seo-title: Políticas de seguridad de contenido y el servicio de identidad de la plataforma de experiencia
title: Políticas de seguridad de contenido y el servicio de identidad de la plataforma de experiencia
uuid: 7399 fed 3-01 c 1-4730-834 e-e 2 dd 2 c 5791 ff
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Políticas de seguridad de contenido y el servicio de identidad de la plataforma de experiencia {#content-security-policies-and-the-experience-cloud-id-service}

Una política de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores control sobre qué tipo de recursos se cargan en una página web. Lea esta sección si utiliza el servicio de ID y tiene CSP estrictas que utilizan listas de elementos permitidos para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe que se enumeran aquí a sus listas de elementos permitidos de CSP.

## Revisión de la CSP {#section-5fde5c00a678455c914b8307a8caab82}

Las CSP utilizan el encabezado HTTP `Content-Security-Policy` para controlar el tipo de recursos que acepta o carga un navegador en una página. La aplicación de una CSP puede ayudarle a impedir lo siguiente:

* Cargar archivos de JavaScript cuando estos son de origen desconocido o no están incluidos en una lista de elementos permitidos.
* Ataques de scripts en sitios cruzados (XXS).
* Ataques de inyección de datos.
* Ataques de &quot;defacement&quot; (desfiguración).
* Propagación de malware.

El uso de CSP es habitual y se entiende perfectamente. La finalidad de esta documentación no es explicar detalladamente las CSP (consulte los vínculos de información relacionada que se muestran más abajo para obtener más información). Lo que es importante es que entienda qué nombres de dominio de Adobe debe agregar a una CSP, si los emplea, y tiene estrictas políticas de seguridad. Agregar estos dominios permite que los navegadores visitantes que acceden a su sitio realicen esas importantes llamadas a los recursos de Experience Cloud que usted utiliza.

## Dominios de Experience Cloud para listas de elementos permitidos {#section-30693e9a96834edfbf04de9e698cf2aa}

Agregue estos nombres de dominio o URL a sus CSP para cada solución o servicio de Experience Cloud de lista que utilice.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solución o servicio de Experience Cloud </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>Modifique su CSP para incluir lo siguiente: </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>Modifique su CSP para incluir <span class="codeph">*.tt.omtrdc.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Servicio de ID de visitante</b> </p> </td> 
   <td colname="col2"> <p>Modifique su CSP para incluir <span class="codeph">*.demdex.net</span>. </p> <p>Las llamadas al dominio <span class="codeph"> demdex. net</span> se utilizan para generar <a href="../introduction/cookies.md" format="dita" scope="local"> las cookies y el servicio de identidad de Experience Platform</a> y para sincronizar ID. Consulte también <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Explicación de las llamadas al dominio Demdex</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_ LIKE_ THIS]
>
>* [Content Security Policy Reference ](https://content-security-policy.com/)(Referencia de política de seguridad de contenido)
>* [MDN: Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) (MDN: Política de seguridad de contenido)
>* [Wikipedia: Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy) (Wikipedia: Política de seguridad de contenido)
