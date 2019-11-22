---
description: 'null'
keywords: order of operations;ID Service
seo-description: 'null'
seo-title: CNAME de recopilación de datos y seguimiento entre dominios
title: CNAME de recopilación de datos y seguimiento entre dominios
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: tm+mt
source-git-commit: 588c4b29ebd3cccea4f2ab032f69a4b6c6e97f2a

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

Analytics utilizará siempre el ID de origen y, si el ID de terceros está habilitado y se presenta, el ID de origen de cada sitio será el mismo. Sin embargo, si la ID de terceros está deshabilitada, ya sea por su configuración o porque el explorador bloquea las cookies de terceros, no hay forma de unir el tráfico de los dos sitios.

## Dominios heredados de Analytics

Antes de que se iniciara el servicio de ID de visitante, hace varios años, muchos clientes utilizaban los dominios de análisis nativos para establecer las cookies de ID. Estos incluyen `omtrdc.net`o `2o7.net` un dominio CNAME. `omtrdc.net`, `2o7.net` y en algunos casos se utiliza un dominio CNAME para almacenar cookies de terceros. Las cookies configuradas de esta manera siempre se han restringido a un único cliente, de modo que los clientes no pueden combinar sus datos entre empresas. Los dominios CNAMED de terceros, a veces denominados dominios de terceros prácticos, solo se utilizan cuando los clientes desean rastrear a los usuarios en los sitios que son propietarios (por ejemplo, ejemplo.com, example.co.jp). Este método está en desuso para permitir un servicio de ID de visitante más robusto y que tenga en cuenta la privacidad. Los clientes deben pasar al servicio de ID de visitante con un CNAME por dominio lo antes posible.

## Proporcione su propia identidad

Si un cliente decide superar por completo el sistema de identificación de Adobe e implementar uno propio mediante un ID [de visitante](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/unique-visitors/visid-custom.md)personalizado. Hay algunas cosas que hay que tener en cuenta si elige esta ruta.

- Deberá implementar la exclusión y los controles de privacidad adecuados
- Ese ID solo se aplicará a Analytics
- Usted es responsable de mantener esa ID

## CNAME de recopilación de datos

Adobe aún recomienda el uso de un CNAME junto con el servicio de ID de visitante. Esto permite que la ID de visitante de origen persista utilizando cookies HTTP, lo que hace que las cookies sean más duraderas.

## Opciones de exclusión

Adobe ofrece las API para compartir señales de exclusión con nuestros sistemas, de modo que pueda proporcionar a los usuarios formas de no realizar el seguimiento. Proporcionamos instrucciones detalladas sobre la [exclusión](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/data-collection/opt-out.md) y la [inclusión](https://docs.adobe.com/content/help/en/id-service/using/implementation-guides/opt-in-service/optin-overview.md)

## Habilitación de la compatibilidad con CNAME con el servicio Experience Cloud ID {#section-25d4feb686d944e3a877d7aad8dbdf9a}

La compatibilidad con CNAME del servidor de recopilación de datos está [habilitada para configurar un CNAME](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.md) y para configurar la `visitor.marketingCloudServerSecure` variable en el servicio de identidad de Experience Cloud y `s.trackingServerSecure` en AppMeasurement.
