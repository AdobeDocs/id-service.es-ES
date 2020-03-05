---
description: Una política de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores control sobre qué tipo de recursos se cargan en una página web. Lea esta sección si utiliza el servicio de ID y tiene CSP estrictas que utilizan listas de elementos permitidos para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe que se enumeran aquí a sus listas de elementos permitidos de CSP.
keywords: ID Service
seo-description: Una política de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores control sobre qué tipo de recursos se cargan en una página web. Lea esta sección si utiliza el servicio de ID y tiene CSP estrictas que utilizan listas de elementos permitidos para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe que se enumeran aquí a sus listas de elementos permitidos de CSP.
seo-title: Políticas de seguridad del contenido y el servicio de Experience Cloud ID
title: Políticas de seguridad del contenido y el servicio de Experience Cloud ID
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: tm+mt
source-git-commit: 7255228470a59a537251c3a3eec686f52a2b76ec

---


# Políticas de seguridad del contenido y el servicio de Experience Cloud ID {#content-security-policies-and-the-experience-cloud-id-service}

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
   <td colname="col1"> <p> <b>Servicio Experience Cloud ID y Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>Modifique el CSP para incluir los dominios siguientes.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Si utiliza Adobe Launch para implementar etiquetas, también deberá agregarlas <code>https://assets.adobedtm.com</code> a la lista de dominios.</li></ul></p> <p>Las llamadas al dominio <span class="codeph">demdex.net</span> se utilizan para generar las cookies <a href="../introduction/cookies.md" format="dita" scope="local"> y el servicio de identidad de Experience Cloud</a> y para sincronizar ID. Consulte también <a href="https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html" format="https" scope="external">Explicación de las llamadas al dominio Demdex</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Complemento Activity Map</b> </p> </td> 
 <td colname="col2"> <p>Modifique su CSP para incluir *.adobe.com. **Nota**: Si ya tenía Activity Map instalado antes de enero de 2020, el explorador seguirá viendo una solicitud inicial a *.omniture.com, pero se redirigirá a *.adobe.com. </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [Content Security Policy Reference ](https://content-security-policy.com/)(Referencia de política de seguridad de contenido)
>* [MDN: Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) (MDN: Política de seguridad de contenido)
>* [Wikipedia: Content Security Policy](https://en.wikipedia.org/wiki/Content_Security_Policy) (Wikipedia: Política de seguridad de contenido)

