---
description: Una directiva de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores el control sobre el tipo de recursos que se cargan en una página web. Lea esta sección si utiliza el servicio de ID y tiene CSP estrictos que utilizan listas de permitidos para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe enumerados aquí a sus listas de permitidos CSP.
keywords: Servicio de ID
title: Políticas de seguridad del contenido y el servicio de identidad de Experience Cloud
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
TQID: https://experienceleague.adobe.com/UX0RWE7v912XEHJCJE49yt1sy13t1P0I0I79gG9Z7m8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 530
ht-degree: 64%

---

# Políticas de seguridad del contenido y el servicio de identidad de Experience Cloud {#content-security-policies-and-the-experience-cloud-id-service}

Una directiva de seguridad de contenido (CSP) es una función de seguridad y encabezado HTTP que proporciona a los navegadores el control sobre el tipo de recursos que se cargan en una página web. Lea esta sección si utiliza el servicio de ID y tiene CSP estrictos que utilizan listas de permitidos para aceptar recursos de dominios de confianza. Deberá agregar los dominios de Adobe enumerados aquí a sus listas de permitidos CSP.

## Revisión de la CSP {#section-5fde5c00a678455c914b8307a8caab82}

Las CSP utilizan el encabezado HTTP `Content-Security-Policy` para controlar el tipo de recursos que acepta o carga un navegador en una página. La aplicación de un CSP puede ayudarle a evitar:

* Que se carguen los archivos JavaScript si el origen es desconocido o no se incluye en una lista de permitidos.
* Ataques de ejecución de scripts en sitios múltiples (XXS).
* Ataques de inyección de datos.
* Ataques de modificación de sitios web.
* Distribución de malware.

El uso de los CSP es habitual y conocido. Esta documentación no tiene por objeto explicar en detalle los CSP (para obtener más información, consulte los vínculos de relacionados). Lo importante es que entienda qué nombres de dominio de Adobe debe agregar a un CSP si los utiliza y tiene políticas de seguridad estrictas. Añadir estos dominios permite a los navegadores de visitante que acceden a su sitio realizar las llamadas importantes a los recursos de Experience Cloud que utilice.

## Dominios de Experience Cloud para Inclusiones en la lista de permitidos {#section-30693e9a96834edfbf04de9e698cf2aa}

Añada estos nombres de dominio o direcciones URL a su CSP para cada solución o servicio de Experience Cloud que utilice.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">Solución o servicio de Experience Cloud</th>
   <th colname="col2" class="entry">Descripción</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>Modifique su CSP para incluir lo siguiente:</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Target</b></p>
   </td>
   <td colname="col2">
    <p>Modifique su CSP para incluir <span class="codeph">*.tt.omtrdc.net</span>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Servicio de Experience Cloud ID y Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>Modifique su CSP para incluir los siguientes dominios.</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>Si utiliza Adobe Launch para implementar etiquetas, también deberá agregar <code>https://assets.adobedtm.com</code> a la lista de dominios.</li>
    </ul>
    <p>Las llamadas al dominio <span class="codeph">demdex.net</span> se usan para generar las <a href="../introduction/cookies.md" format="dita" scope="local">cookies y el servicio de identidad de Experience Cloud</a> y para sincronizar ID. Vea también <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=es" format="https" scope="external">Explicación de las llamadas al dominio Demdex</a>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Complemento de Activity Map</b></p>
   </td>
   <td colname="col2">
    <p>Modifique su CSP para incluir *.adobe.com. **Nota**: Si ya tenía Activity Map instalado antes de enero de 2020, el explorador seguirá viendo una solicitud inicial a *.omniture.com, pero se redirigirá a *.adobe.com.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>Si restringe los parámetros de cadena de consulta, lista de permitidos los siguientes parámetros:</p>
    <ul>
     <li><code>s_kwcid</code> (que usa <code>!</code>)</li>
     <li><code>ef_id</code> (que usa <code>:</code>)</li>
    </ul>
    <p>Si bloquea el carácter <code>!</code> en las direcciones URL, lista de permitidos también.</p>
    <p>Advertising Analytics solo usa <code>s_kwcid</code>, pero Advertising Search, Social y Commerce, y Advertising DSP también usan <code>ef_id</code>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>Modifique su CSP para incluir los siguientes dominios:</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [Referencia de política de seguridad de contenido](https://content-security-policy.com/)
>* [MDN: Política de seguridad de contenido](https://developer.mozilla.org/es/docs/Web/HTTP/CSP)
>* [Wikipedia: Política de seguridad de contenido](https://en.wikipedia.org/wiki/Content_Security_Policy)

