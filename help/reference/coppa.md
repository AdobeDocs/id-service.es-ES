---
description: La Ley de Protección de la Privacidad Infantil en Línea (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de Experience Cloud ID que impide que establezca cookies en el dominio de terceros de un navegador.
keywords: ID Service
seo-description: La Ley de Protección de la Privacidad Infantil en Línea (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de Experience Cloud ID que impide que establezca cookies en el dominio de terceros de un navegador.
seo-title: Compatibilidad con COPPA en el servicio de Experience Cloud ID
title: Compatibilidad con COPPA en el servicio de Experience Cloud ID
uuid: 621b5ebd-92e7-4635-be85-8d7e36589fcb
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 77%

---


# Compatibilidad con COPPA en el servicio de Experience Cloud ID {#coppa-support-in-the-experience-cloud-id-service}

La Ley de Protección de la Privacidad Infantil en Línea (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de Experience Cloud ID que impide que establezca cookies en el dominio de terceros de un navegador.

>[!NOTE]
>
>Para la versión 3.0.0 o superior.

**Cookies y seguimiento**

Cuando se carga una página web, el servicio de ID de [!DNL Experience Cloud] llama a un servidor de recopilación de datos (DCS) de [!DNL Adobe]. La respuesta de DCS incluye una cookie de Experience Cloud y una cookie demdex.net.

* La cookie de Experience Cloud se establece en el dominio de origen. No se puede usar para rastrear visitantes en distintos dominios, a menos que esos dominios trabajen juntos para permitir el acceso.
* La cookie demdex.net se establece en el dominio de terceros. Contiene un identificador único que puede utilizarse para rastrear visitantes en distintos dominios.

**Cumplimiento de Cookies y COPPA**

Las cookies de terceros que rastrean visitantes en diferentes dominios en sitios web dirigidos a (o principalmente a) niños, activan los requisitos de consentimiento paterno de COPPA. Con el fin de facilitar el cumplimiento de la ley COPPA para el análisis interno de sitios web, añada la variable `disableThirdPartyCookies:true` a la `Visitor.getInstance` función, como se muestra a continuación.

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

