---
description: Estas instrucciones, herramientas y procedimientos le ayudan a determinar si el servicio de ID está funcionando correctamente. Estas pruebas se aplican al servicio de ID en general y a diferentes combinaciones de servicios de ID y soluciones de Experience Cloud.
keywords: ID Service
seo-description: Estas instrucciones, herramientas y procedimientos le ayudan a determinar si el servicio de ID está funcionando correctamente. Estas pruebas se aplican al servicio de ID en general y a diferentes combinaciones de servicios de ID y soluciones de Experience Cloud.
seo-title: Comprobación y verificación del servicio de identidad de Experience Cloud
title: Comprobación y verificación del servicio de Experience Cloud ID
uuid: 442de9c3-c265-4412-89bd-aeaa286ddad6
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Comprobación y verificación del servicio de identidad de Experience Cloud{#test-and-verify-the-experience-cloud-id-service}

Estas instrucciones, herramientas y procedimientos le ayudan a determinar si el servicio de ID está funcionando correctamente. Estas pruebas se aplican al servicio de ID en general y a diferentes combinaciones de servicios de ID y soluciones de Experience Cloud.

## Antes de empezar {#section-b1e76ad552ed4eb793b6e521a55127d4}

Información importante necesaria antes de comenzar a probar y verificar el servicio de ID.

**Entornos de exploradores**

Cuando realice pruebas en una sesión normal del explorador, borre la caché del explorador antes de cada prueba.

También puede probar el servicio de ID en una sesión anónima o de incógnito del explorador. En una sesión anónima, no es necesario borrar las cookies del explorador o la caché antes de cada prueba.

**Herramientas**

La [herramienta de depuración de Adobe](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html) y el [proxy HTTP Charles](https://www.charlesproxy.com/) pueden ayudarle a determinar si el servicio de ID se ha configurado para funcionar correctamente con Analytics. La información de esta sección se basa en los resultados devueltos por el depurador de Adobe y Charles. No obstante, es libre de usar la herramienta o el depurador que más le convenga.

## Pruebas con la herramienta de depuración de Adobe {#section-861365abc24b498e925b3837ea81d469}

Su integración del servicio se ha configurado correctamente cuando aparece un [!DNL Experience Cloud ID] (MID) en la respuesta de la herramienta de depuración de [!DNL Adobe]. Consulte [Cookies y el servicio de identidad de Experience Cloud](../introduction/cookies.md) para obtener más información sobre el MID.

Para verificar el estado del servicio de ID con la herramienta [!DNL Adobe] [Debugger](https://docs.adobe.com/content/help/en/analytics/implementation/validate/debugger.html):

1. Borre las cookies del explorador o abra una sesión de navegación anónima.
1. Cargue la página de prueba que contiene el código del servicio de ID.
1. Abra la herramienta [!DNL Adobe] Debugger.
1. Busque en los resultados un MID.

## Comprender los resultados de Adobe Debugger {#section-bd2caa6643d54d41a476d747b41e7e25}

El MID se almacena en un par clave-valor que sigue esta sintaxis: `MID= *`Experience Cloud ID`*`. El depurador muestra esta información tal y como se ve a continuación.

**Correcto**

El servicio de ID se ha implementado correctamente si ve una respuesta similar a esta:

```
mid=20265673158980419722735089753036633573
```

Si es cliente de [!DNL Analytics], es posible que vea un ID de [!DNL Analytics] (AID) además del MID. Esto sucede:

* Con algunos de los visitantes iniciales y prolongados del sitio.
* Si tiene un período de gracia habilitado.

**Fallo**

Póngase en contacto con [el servicio de atención](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) al cliente si el depurador:

* No devuelve un MID.
* Devuelve un mensaje de error que indica que el ID de socio no se ha aprovisionado.

## Pruebas con el proxy HTTP Charles {#section-d9e91f24984146b2b527fe059d7c9355}

Para comprobar el estado del servicio de ID con Charles:

1. Borre las cookies del explorador o abra una sesión de navegación anónima.
1. Inicio Charles.
1. Cargue la página de prueba que contiene el código del servicio de ID.
1. Compruebe las llamadas de solicitud y respuesta y los datos que se describen a continuación.

## Comprender los resultados de Charles {#section-c10c3dc0bb9945cbaffcf6fec7082fab}

Consulte esta sección para ver información sobre dónde y qué buscar al usar Charles para supervisar las llamadas HTTP.

**Solicitudes del servicio de ID correctas en Charles**

El código del servicio de ID funciona correctamente cuando la función `Visitor.getInstance` realiza una llamada de JavaScript a `dpm.demdex.net`. Las respuestas correctas incluirán su [identificador de organización](../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26). El identificador de organización se transfiere como par clave-valor con esta sintaxis: `d_orgid= *`ID de organización`*`. Busque `dpm.demdex.net` y las llamadas de JavaScript en la ficha [!UICONTROL Estructura]. Busque su identificador de organización en la ficha [!UICONTROL Solicitud].

![](assets/charles_request.png)

**Respuestas del servicio de ID correctas en Charles**

Su cuenta se ha aprovisionado correctamente para el servicio de ID cuando la respuesta de los [servidores de recopilación de datos](https://docs.adobe.com/content/help/en/audience-manager/user-guide/reference/system-components/components-data-collection.html) (DCS) devuelve un MID. El MID se devuelve en un par clave-valor que sigue esta sintaxis: `d_mid: *`Experience Cloud ID de visitante`*`. Busque el MID en la ficha [!UICONTROL Respuesta], tal y como se ve a continuación.

![](assets/charles_response_success.png)

**Respuestas del servicio de ID incorrectas en Charles**

Su cuenta no se ha aprovisionado correctamente si el MID no aparece en la respuesta de los DCS. An unsuccessful response returns an error code and message in the [!UICONTROL Response] tab as shown below. Póngase en contacto con el Servicio de atención al cliente si aparece este mensaje de error en la respuesta del DCS.

![](assets/charles_response_unsuccessful.png)

For more information about error codes, see [DCS Error Codes, Messages, and Examples](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-api-reference/dcs-error-codes.html).
