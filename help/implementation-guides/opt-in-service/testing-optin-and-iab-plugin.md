---
description: Una vez que haya habilitado el servicio de inclusión (Opt-in) en su sitio web, utilice los métodos de validación y las herramientas de desarrollo de su navegador para comprobar que el servicio funcione correctamente.
seo-description: Una vez que haya habilitado el servicio de inclusión (Opt-in) en su sitio web, utilice los métodos de validación y las herramientas de desarrollo de su navegador para comprobar que el servicio funcione correctamente.
seo-title: Validación del servicio de inclusión (Opt-in)
title: Validación del servicio de inclusión (Opt-in)
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 36%

---


# Validación del servicio de inclusión (Opt-in){#validating-opt-in-service}

Una vez que haya habilitado el servicio de inclusión (Opt-in) en su sitio web, utilice los métodos de validación y las herramientas de desarrollo de su navegador para comprobar que el servicio funcione correctamente.

## Caso de uso 1: Habilitar el servicio de inclusión (Opt-in) {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Antes de cargar la página, borre la caché y las cookies.

En Chrome, haga clic con el botón derecho en la página web y seleccione Inspect. Como en la captura de pantalla de arriba, seleccione la ficha *Red* para vista de las solicitudes realizadas desde el explorador.

En el ejemplo anterior, se han instalado en la página las etiquetas JS de Adobe siguientes: ECID, AAM, Analytics y Destinatario.

**Método para comprobar si el servicio de inclusión (Opt-in) está funcionando correctamente:**

No debería ver ninguna solicitud a los servidores Adobe:

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>Podría ver una llamada a `http://dpm.demdex.net/optOutStatus`, un extremo de SOLO LECTURA que se utiliza para recuperar el estado de exclusión del visitante. Este extremo no dará como resultado que se creen cookies de terceros y no recopilará ninguna información de la página.

No debería ver ninguna cookie creada por las etiquetas Adobe: (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

En Chrome, vaya a la ficha *Aplicación* , expanda la sección *Cookies* en *Almacenamiento* y seleccione el nombre de dominio del sitio web:

![](assets/use_case_1_2.png)

## Caso de uso 2: Habilitar Opt-in y almacenamiento  {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

La única diferencia en el caso de uso 2 es que verá *una nueva cookie* que contiene los permisos de Opt-in que el visitante ha proporcionado: **adobeujs-optin**

## Caso de uso 3: Habilitar Opt-in y preaprobar Adobe Analytics  {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Dado que Adobe Analytics ya ha aprobado la opción de inclusión, verá las solicitudes en la ficha Red al servidor de seguimiento:

![](assets/use_case_3_1.png)

y verá las cookies de Analytics en la ficha Aplicación:

![](assets/use_case_3_2.png)

## Caso de uso 4: Habilitar Opt-in e IAB  {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Cómo vista su consentimiento actual de IAB en la página:**

Abra las herramientas del desarrollador y seleccione la ficha *Consola* . Pegue el siguiente fragmento de código y pulse Intro:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

A continuación se muestra un ejemplo de salida cuando se aprueban los propósitos 1, 2 y 5 y se aprueba el ID de proveedor de Audience Manager:

* demdex.net/id: La presencia de esta llamada prueba que ECID ha solicitado un ID a demdex.net
* demdex.net/event: La presencia de esta llamada prueba que la llamada de recopilación de datos del DIL funciona según lo esperado.
* demdex.net/dest5.html: La presencia de esta llamada prueba que se están activando las sincronizaciones de ID.

![](assets/use_case_4_1.png)

Si una de las siguientes opciones no es válida, no verá ninguna solicitud a los servidores Adobe ni ninguna cookie de Adobe:

* No se aprueban los fines 1, 2 ó 5.
* El ID de proveedor de Audience Manager no está aprobado.