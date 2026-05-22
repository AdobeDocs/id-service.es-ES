---
description: La Ley de Protección de la Privacidad Infantil en Línea (Children's Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de identidad de Experience Cloud que impide que establezca cookies en el dominio de terceros de un navegador.
keywords: Servicio de ID
title: Compatibilidad con COPPA en el servicio de identidad de Experience Cloud
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
TQID: https://experienceleague.adobe.com/szz7syrA2KSDasXTox02PTbxBy60tfFc80hHmsjXwc0
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080bid: d3cdead0-685a-4489-9250-4bb709942f66id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 357
ht-degree: 86%

---

# Compatibilidad con COPPA en el servicio de identidad de Experience Cloud {#coppa-support-in-the-experience-cloud-id-service}

La Ley de Protección de la Privacidad Infantil en Línea (Children&#39;s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de identidad de Experience Cloud que impide que establezca cookies en el dominio de terceros de un navegador.

>[!NOTE]
>
>Para la versión 3.0.0 o superior.

**Cookies y seguimiento**

Cuando se carga una página web, el servicio de ID de [!DNL Experience Cloud] llama a un servidor de recopilación de datos (DCS) de [!DNL Adobe]. La respuesta del DCS incluye una cookie de Experience Cloud y una cookie demdex.net.

* La cookie de Experience Cloud se establece en el dominio de origen. No se puede usar para rastrear visitantes entre dominios diferentes, a menos que dichos dominios trabajen juntos para permitir el acceso.
* La cookie demdex.net se establece en el dominio de terceros. Contiene un identificador único que puede utilizarse para rastrear visitantes entre dominios diferentes.

**Cookies y cumplimiento de requisitos de la ley COPPA**

Las cookies de terceros que rastrean visitantes entre dominios distintos en sitios web dirigidos a niños (o principalmente para niños), desencadenan requisitos de consentimiento paterno en virtud de la ley COPPA. Con el fin de facilitar el cumplimiento de la ley COPPA para el análisis interno de sitios web, añada la variable `disableThirdPartyCookies:true` a la `Visitor.getInstance` función, como se muestra a continuación.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Cuando se establece en `true`, el `disableThirdPartyCookies` objeto evita que el DCS devuelva la cookie demdex.net de terceros. Si el visitante de un sitio tiene ya esta cookie en su navegador, el servicio de ID no la usará para crear un nuevo ID de [!DNL Experience Cloud] o devolver un ID existente. En lugar de eso, el servicio de [!DNL Experience Cloud] ID de crea un ID aleatorio nuevo en la cookie de origen. Una vez activado, pueden recopilarse datos con el servicio de ID para compartirlos en distintas [!DNL Experience Cloud] soluciones de, además de otras operaciones internas permitidas por COPPA.

>[!MORELIKETHIS]
>
>* [Centro de privacidad de Adobe](http://www.adobe.com/es/privacy.html)
>* [¿Qué es COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

