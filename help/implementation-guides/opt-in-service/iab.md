---
description: Conecte su plataforma de administración de consentimiento (CMP) con el complemento de Audience Manager de inclusión para el marco de transparencia y consentimiento de IAB (TCF).
title: Uso de servicios de inclusión con IAB Framework
exl-id: 9ac9b232-0797-4e77-a611-9cf5d17a5cb7
TQID: https://experienceleague.adobe.com/70QH1BoRSSbiw7cMfRjrHmiSxQLbuiHcWAG5b-xVOLw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 515
ht-degree: 94%

---

# Uso de servicios de inclusión con IAB Framework{#using-opt-in-services-with-iab-framework}

>[!IMPORTANT]
>
>El siguiente documento solo se aplica a IAB 2.0. Los usuarios deben utilizar Visitor.js versión 5.0 para trabajar con IAB 2.0.

Conecte la plataforma de administración de consentimiento (CMP) con el plugin del marco de transparencia y consentimiento (TCF) de IAB de inclusión.

Los clientes de Adobe Audience Manager que utilizan [IAB TCF](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/) pueden conectar su plataforma de administración de consentimiento (CMP) con el complemento IAB TCF de inclusión. El servicio de inclusión (Opt-in) es una función integrada en la biblioteca JavaScript de ECID que puede deshabilitar bibliotecas determinadas de soluciones de Adobe, en función de las preferencias del visitante, que se establecen dentro de una plataforma CMP. Cuando se implementa el complemento IAB TCF de inclusión con la biblioteca ECID, las preferencias de visitante de su CMP compatible con IAB TCF se asignan automáticamente al servicio de inclusión. Estas preferencias habilitarán bibliotecas basadas en Audience Manager (DIL y ECID) y llamadas asociadas cuando se reciba el consentimiento.

## Implementar una CMP compatible con IAB {#section-9fd2403b548947dbb1921ac6ff9d0c82}

Para que la inclusión se integre con el consentimiento IAB TCF, necesita completar las siguientes acciones:

1. Implemente una CMP que sea compatible con IAB y esté registrada como proveedor IAB, o desarrolle una CMP interna que implemente la especificación IAB y, a continuación, regístrela como CMP en IAB TCF.
1. Defina/Cargue `__tcfapi` antes de cargar Adobe JS.

Para obtener más información, consulte los [documentos del Interactive Advertising Bureau](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework/blob/master/TCFv2/TCF-Implementation-Guidelines.md).

## Habilitar el complemento IAB TCF de inclusión dentro de su biblioteca JavaScript de ECID {#section-77bf1b9ed67241a59e56c21ab752e82f}

>[!NOTE]
>
>El servicio de inclusión (Opt-in) solo está disponible en la versión de ECID 4.0 y posteriores.

Utilice etiquetas para implementar el complemento IAB TCF de inclusión para su sitio. Al habilitar IAB para la opción de inclusión de forma manual, asegúrese de que la siguiente configuración se establezca en true en el objeto Visitante:

```javascript
Visitor.getInstance("YOUR_ORG_ID", {  
  doesOptInApply: true,
  isIabContext: true
});
```

Una vez que la configuración sea correcta, las bibliotecas ECID y DIL se habilitarán o deshabilitarán según los criterios de consentimiento de CMP y IAB TCF.

>[!IMPORTANT]
>
>Audience Manager necesita consentimiento para las *Finalidades 1 y 10, además del consentimiento del proveedor*, para poder implementar cookies e iniciar o cumplir sincronizaciones de ID. Obtenga más información sobre el complemento IAB TCF de inclusión en la documentación de Audience Manager [aquí](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=es).

Para obtener más información sobre cómo se valida el complemento de IAB TCF de inclusión, consulte el caso n.º 4 de la guía de validación [aquí](../../implementation-guides/opt-in-service/testing-optin-and-iab-plugin.md#section-ca5c6f92fbdf4fd29b4acb6b644efbd0).

## Documentación relacionada {#section-55da1110051a4b39b1037803f4a7b264}

* [Marco de transparencia y consentimiento (TCF) de IAB](https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/): para obtener más información sobre el IAB estándar
* [Adobe Opt-In](../../implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360): para obtener más información acerca de Opt-In, un componente necesario para la gestión del consentimiento en las soluciones de plataforma
* Compatibilidad con el marco de transparencia y consentimiento IAB (TCF) [en Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/overview/data-privacy/consent-management/aam-iab-plugin.html?lang=es)
* [Sus decisiones de privacidad](https://www.adobe.com/es/privacy/opt-out.html#customeruse): otra opción de privacidad a disposición de los usuarios es la capacidad de excluirse de toda recopilación de datos mediante otras herramientas globales de exclusión. La exclusión global tiene preferencia sobre la verificación mediante inclusión e IAB TCF

