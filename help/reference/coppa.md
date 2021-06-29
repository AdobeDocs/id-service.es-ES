---
description: La Ley de Protección de la Privacidad Infantil en Línea (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de Experience Cloud ID que impide que establezca cookies en el dominio de terceros de un navegador.
keywords: Servicio de ID
title: Compatibilidad con COPPA en el servicio de Experience Cloud ID
exl-id: c7579f90-3011-4e26-b908-08907bf12ba2
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '343'
ht-degree: 100%

---

# Compatibilidad con COPPA en el servicio de Experience Cloud ID {#coppa-support-in-the-experience-cloud-id-service}

La Ley de Protección de la Privacidad Infantil en Línea (Children’s Online Privacy Protection Act, o COPPA) prohíbe la obtención de información personal de niños menores de 13 años en línea y sin el previo consentimiento paterno verificable. Los clientes afectados por esta ley pueden agregar una variable opcional al código de su servicio de Experience Cloud ID que impide que establezca cookies en el dominio de terceros de un navegador.

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

