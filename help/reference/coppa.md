---
description: La  Ley de Protección de la Privacidad Infantil en Línea  (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes interesados en COPPA pueden agregar una variable opcional a su código de servicio de identidad de la plataforma de experiencias que evita que pueda configurar cookies en el dominio de terceros de un navegador.
keywords: Servicio de ID
seo-description: La  Ley de Protección de la Privacidad Infantil en Línea  (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes interesados en COPPA pueden agregar una variable opcional a su código de servicio de identidad de la plataforma de experiencias que evita que pueda configurar cookies en el dominio de terceros de un navegador.
seo-title: Compatibilidad con COPPA en el servicio de identidad de la plataforma de experiencia
title: Compatibilidad con COPPA en el servicio de identidad de la plataforma de experiencia
uuid: 621 b 5 ebd -92 e 7-4635-be 85-8 d 7 e 36589 fcb
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Compatibilidad con COPPA en el servicio de identidad de la plataforma de experiencia {#coppa-support-in-the-experience-cloud-id-service}

La  Ley de Protección de la Privacidad Infantil en Línea  (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes interesados en COPPA pueden agregar una variable opcional a su código de servicio de identidad de la plataforma de experiencias que evita que pueda configurar cookies en el dominio de terceros de un navegador.

>[!NOTE]
>
>Para la versión 1.5.3 o superior.

**Cookies y seguimiento**

Cuando se carga una página web, el servicio de ID de [!DNL Experience Cloud] llama a un servidor de recopilación de datos (DCS) de [!DNL Adobe]. La respuesta del DCS incluye una cookie de Experience Cloud y una cookie demdex.net.

* La cookie de Experience Cloud se establece en el dominio de origen. No puede utilizarse para seguir a visitantes entre dominios distintos, a menos que dichos dominios colaboren juntos para permitir el acceso.
* La cookie demdex.net se establece en el dominio externo. Contiene un identificador único que puede emplearse para seguir a visitantes entre dominios distintos.

**Cookies y cumplimiento con COPPA**

Las cookies de terceros que siguen a visitantes entre distintos dominios en sitios web dirigidos a niños (o que son principalmente para niños) activan requisitos de consentimiento paterno de COPPA. Con el fin de facilitar el cumplimiento de la ley COPPA para el análisis interno de sitios web, añada la variable `disableThirdPartyCookies:true` a la función `Visitor.getInstance`, como se muestra a continuación.

```js
//Call the ID service 
var visitor = Visitor.getInstance("insert marketing cloud ID here", { 
 
    //Set disableThirdPartyCookies configuration param 
    disableThirdPartyCookies: true 
 
    ... 
});
```

Cuando se establece en `true`, el objeto `disableThirdPartyCookies` evita que el DCS devuelva la cookie demdex.net de terceros. Si el visitante de un sitio tiene ya esta cookie en su navegador, el servicio de ID no la usará para crear un nuevo ID de [!DNL Experience Cloud] o devolver un ID existente. En lugar de eso, el servicio de ID de [!DNL Experience Cloud] crea un ID aleatorio nuevo en la cookie de origen. Una vez activado, pueden recopilarse datos con el servicio de ID para compartirlos en distintas soluciones de [!DNL Experience Cloud], además de otras operaciones internas permitidas por COPPA.

>[!MORE_ LIKE_ THIS]
>
>* [Centro de privacidad de Adobe](http://www.adobe.com/privacy.html)
>* [¿Qué es COPPA?](http://www.consumer.ftc.gov/articles/0031-protecting-your-childs-privacy-online#whatis)

