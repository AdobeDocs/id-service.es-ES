---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: CNAME de recopilación de datos y seguimiento entre dominios
title: CNAME de recopilación de datos y seguimiento entre dominios
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 989b5f537848a7506a96e2eac17409f8b0307217

---


# Recopilación de datos e identidad{#data-collection-and-identity}

En Analytics hay tres formas de identificar a los visitantes.

- Usar el servicio de ID de [visitante](https://docs.adobe.com/content/help/en/id-service/using/home.md)
- Uso del ID de visitante de Analytics [heredado](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-overview.md)
- Proporcionar su propia identidad

## Usaban el servicio de identificación del cliente{#using-the-visitor-id-service}

El servicio de ID de visitante es la manera recomendada de identificar a los visitantes. Se basa en dos componentes

- ID de origen: ID de origen que se puede utilizar para medir los visitantes de su propio sitio web. Este ID se almacena en el ID del primer elemento, tanto en una cookie del lado del cliente como en una cookie del lado del servidor (con un CNAME).
- ID de terceros (opcional): ID de terceros independiente almacenada en demdex.net que se puede utilizar para medir visitantes en varios dominios (por ejemplo, ejemplo.com y ejemplo.net)

Analytics usará el ID de origen a menos que se habiliten ID de terceros, y entonces los exploradores lo permitirán. El ID de terceros se respeta antes del cliente, de modo que un cliente no puede combinar datos con otro cliente en Analytics.

## Dominios heredados de Analytics

Antes del inicio del servicio de ID de visitante de Adobe, muchos clientes utilizaban los dominios de análisis nativos para establecer las cookies de ID. Estos incluyen `omtrdc.net`o `2o7.net` un dominio CNAME. `omtrdc.net`, `2o7.net`, en algunos casos se utilizó un dominio CNAME para almacenar cookies de terceros. Las cookies configuradas de esta manera se restringieron a un único cliente para que los clientes no pudieran combinar sus datos con los datos de otros clientes. Los dominios CNAMED de terceros, a veces denominados dominios de terceros prácticos, se utilizaban cuando los clientes deseaban rastrear a los usuarios en los sitios que poseían (por ejemplo, ejemplo.com, example.co.jp). Este método o el uso de CNAME para admitir dominios de terceros prácticos está en desuso para permitir un servicio de ID de visitante más robusto y que tenga en cuenta la privacidad. Los clientes deben pasar al servicio de ID de visitante con un CNAME por dominio lo antes posible.

## Proporcione su propia identidad

Si un cliente decide superar por completo el sistema de identificación de Adobe e implementar uno propio mediante un ID [de visitante](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)personalizado. Hay algunas cosas que hay que tener en cuenta si elige esta ruta.

- Deberá implementar la exclusión y los controles de privacidad adecuados
- Ese ID solo se aplicará a Analytics
- Usted es responsable de mantener esa ID

## CNAME de recopilación de datos

Adobe aún recomienda el uso de un CNAME junto con el servicio de ID de visitante. Esto permite que la ID de visitante de origen persista utilizando cookies HTTP, lo que hace que las cookies sean más duraderas.

## OPTOUT

Adobe proporciona a los clientes las API para compartir señales de exclusión con nuestros sistemas, de modo que los clientes puedan permitir a los usuarios no realizar el seguimiento. Proporcionamos instrucciones detalladas sobre cómo el cliente puede implementar los controles adecuados para apoyar la elección del usuario; ya sea la API [de](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) exclusión o las opciones para [evitar que la cookie se active](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md) hasta que se obtenga el consentimiento

## Habilitación de la compatibilidad con CNAME con el servicio Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

La compatibilidad con CNAME del servidor de recopilación de datos está [habilitada para configurar un CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) y para configurar la `visitor.marketingCloudServerSecure` variable en el servicio de identidad de Experience Cloud y `s.trackingServerSecure` en AppMeasurement.
