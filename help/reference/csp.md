---
description: Una directiva de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores el control sobre el tipo de recursos que se cargan en una página web. Revise esta sección si utiliza el servicio de ID y tiene CSP estrictos que utilizan listas blancas para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe enumerados aquí a las listas blancas de CSP.
keywords: ID Service
seo-description: Una directiva de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores el control sobre el tipo de recursos que se cargan en una página web. Revise esta sección si utiliza el servicio de ID y tiene CSP estrictos que utilizan listas blancas para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe enumerados aquí a las listas blancas de CSP.
seo-title: Políticas de seguridad del contenido y el servicio de Experience Cloud ID
title: Políticas de seguridad del contenido y el servicio de Experience Cloud ID
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: ht
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: ht
source-wordcount: '619'
ht-degree: 100%

---


# Políticas de seguridad del contenido y el servicio de Experience Cloud ID {#content-security-policies-and-the-experience-cloud-id-service}

Una directiva de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores el control sobre el tipo de recursos que se cargan en una página web. Revise esta sección si utiliza el servicio de ID y tiene CSP estrictos que utilizan listas blancas para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe enumerados aquí a las listas blancas de CSP.

## Revisión de la CSP {#section-5fde5c00a678455c914b8307a8caab82}

Las CSP utilizan el encabezado HTTP `Content-Security-Policy` para controlar el tipo de recursos que acepta o carga un navegador en una página. La aplicación de un CSP puede ayudarle a evitar:

* Que se carguen los archivos JavaScript si el origen es desconocido o no se incluye en una lista blanca.
* Ataques de ejecución de scripts en sitios múltiples (XXS).
* Ataques de inyección de datos.
* Ataques de modificación de sitios web.
* Distribución de malware.

El uso de los CSP es habitual y conocido. Esta documentación no tiene por objeto explicar en detalle los CSP (para obtener más información, consulte los vínculos de relacionados). Lo importante es que entienda qué nombres de dominio de Adobe debe agregar a un CSP si los utiliza y tiene políticas de seguridad estrictas. Añadir estos dominios permite a los navegadores de visitante que acceden a su sitio realizar las llamadas importantes a los recursos de Experience Cloud que utilice.

## Dominios de Experience Cloud para listas de elementos permitidos {#section-30693e9a96834edfbf04de9e698cf2aa}

Añada estos nombres de dominio o direcciones URL a su CSP para cada solución o servicio de Experience Cloud que utilice.

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
   <td colname="col1"> <p> <b>Servicio de Experience Cloud ID y Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>Modifique su CSP para incluir los siguientes dominios.</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Si utiliza Adobe Launch para implementar etiquetas, también deberá agregar <code>https://assets.adobedtm.com</code> a la lista de dominios.</li></ul></p> <p>Las llamadas al dominio <span class="codeph">demdex.net</span> se utilizan para generar las <a href="../introduction/cookies.md" format="dita" scope="local">cookies y el servicio de identidad de Experience Cloud</a> y para sincronizar ID. Consulte también <a href="https://docs.adobe.com/content/help/es-ES/audience-manager/user-guide/reference/demdex-calls.html" format="https" scope="external">Explicación de las llamadas al dominio Demdex</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Complemento Activity Map</b> </p> </td> 
 <td colname="col2"> <p>Modifique su CSP para incluir *.adobe.com. **Nota**: Si ya tenía Activity Map instalado antes de enero de 2020, el explorador seguirá viendo una solicitud inicial a *.omniture.com, pero se redirigirá a *.adobe.com. </p></td> 
 </tr>
 <tr>
 <td colname="col1"> <p> <b>Advertising Analytics</b> </p> </td> 
 <td colname="col2"> <p>Si tiene controles en los parámetros de cadena de consulta, asegúrese de incluir en la lista blanca los parámetros “s_kwcid” y “ef_id”. Técnicamente, Advertising Analytics solo utiliza “s_kwcid”, pero si elige Ad Cloud Search o DSP, también utilizará “ef_id”. Estos parámetros de cadena de consulta son alfanuméricos. El parámetro “s_kwcid” utiliza el parámetro “!” y el parámetro “ef_id” utiliza el carácter “:”. Si está bloqueando el “!” en la dirección URL, también debe incluirlo en la lista de admitidos.</p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>
>* [Referencia de política de seguridad de contenido](https://content-security-policy.com/)
>* [MDN: Política de seguridad de contenido](https://developer.mozilla.org/es/docs/Web/HTTP/CSP)
>* [Wikipedia: Política de seguridad de contenido](https://en.wikipedia.org/wiki/Content_Security_Policy)

