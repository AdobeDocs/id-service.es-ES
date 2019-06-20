---
description: Estas instrucciones están destinadas a los clientes de Analytics que desean utilizar el servicio Experience Cloud ID y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
keywords: Servicio de ID
seo-description: Estas instrucciones están destinadas a los clientes de Analytics que desean utilizar el servicio Experience Cloud ID y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
seo-title: Implementación del servicio Experience Cloud ID para Analytics
title: Implementación del servicio Experience Cloud ID para Analytics
uuid: 7 fbd 6 fa 0-1713-4232-8680-500 ed 62709 d 5
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementación del servicio Experience Cloud ID para Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Estas instrucciones están destinadas a los clientes de Analytics que desean utilizar el servicio Experience Cloud ID y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.

>[!IMPORTANT]
>
>* [Lea los requisitos](../reference/requirements.md) antes de comenzar.
>* Configure y pruebe este código en un entorno de desarrollo antes de implementarlo en producción.
>



Siga estos pasos para implementar el servicio de ID para Adobe Analytics:

1. [Descargar el código del servicio de ID](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Agregar la función Visitor. getinstance al código de servicio de ID](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Add your Experience Cloud Organization ID to Visitor. getinstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Adición de los servidores de seguimiento a Visitor. getinstance](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Actualizar el archivo appmeasurement. js o s_ code. js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Agregar código de API de visitante a la página](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Opcional) Configure un período de gracia](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Probar e implementar el código del servicio de ID](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Step 1: Download the ID Service code {#section-ead9403a6b7e45b887f9ac959ef89f7f}

[!DNL ID Service] La biblioteca de `VisitorAPI.js` código requiere. Para descargar esta biblioteca de códigos:

1. Go to **[!UICONTROL Admin]** &gt; **[!UICONTROL Code Manager]**.
1. In [!DNL Code Manager], click either **[!UICONTROL JavaScript (New)]** or **[!UICONTROL JavaScript (Legacy)]**.

   Se descargarán las bibliotecas de códigos comprimidas.

1. Descomprima el archivo de códigos y abra el archivo `VisitorAPI.js`.

## Paso 2: Add the Visitor.getInstance function to the ID Service Code {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Las versiones anteriores de la API del servicio de ID ubicaban esta función en un lugar distinto y requerían una sintaxis diferente. Si va a migrar desde una versión anterior a la [versión 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), anote la nueva ubicación y la sintaxis documentadas aquí.
>* El código que aparece TODO EN MAYÚSCULAS funciona como marcador de posición para valores reales. Sustituya este texto por el ID de su organización, la URL del servidor de seguimiento u otro valor con nombre.
>



**Parte 1: Copia de la función Visitor.getInstance a continuación**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Parte 2: Adición del código de función al archivo VisitorAPI.js**

Coloque la función `Visitor.getInstance` al final del archivo, después del bloque de códigos. El archivo editado debería tener un aspecto similar a este:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. Si no conoce su ID de organización, puede encontrarlo en la página de administración de [!DNL Experience Cloud]. Consulte también [Administración - Servicios principales](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). Su función editada podría tener un aspecto similar al ejemplo siguiente.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*No* cambie el caso de los caracteres del identificador de organización. El ID distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

## Step 4: Add your tracking servers to Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Los servidores de seguimiento se emplean para la recopilación de datos de [!DNL Analytics].

**Parte 1: Búsqueda de las URL de su servidor de seguimiento**

Check your `s_code.js` or `AppMeasurement.js` files to find the tracking server URLs. Buscará las URL especificadas por estas variables:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: Establecimiento de variables del servidor de seguimiento**

Para determinar las variables del servidor de seguimiento que se van a emplear:

1. Responda las preguntas de la matriz de decisión siguiente. Use las variables que se correspondan con las respuestas.
1. Sustituya los marcadores del servidor de seguimiento por las URL de su servidor de seguimiento.
1. Elimine las variables del servidor de seguimiento y del servidor de [!DNL Experience Cloud] no utilizadas del código.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>When used, match the [!DNL Experience Cloud] server URLs to their corresponding tracking server URLs like this: &gt;
>* [!DNL Experience Cloud] URL del servidor = URL del servidor de seguimiento
>* [!DNL Experience Cloud] URL segura del servidor = URL segura del servidor de seguimiento
>



If you&#39;re not sure how to find your tracking server see the [FAQ](../faq-intro/faq.md) and [Correctly Populate the trackingServer and trackingServerSecure variables](https://helpx.adobe.com/analytics/kb/determining-data-center.html#).

## Step 5: Update your AppMeasurement.js or s_code.js file {#section-b53113aea1bd4de896e0e4e9a7edee19}

Add this function to your `AppMeasurement.js` or `s_code.js` file:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Place the code in the same section that contains configurations such as `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

***(Opcional, pero recomendada)*Cree una variable prop personalizada**

Set a custom prop in `AppMeasurement.js` or `s_code.js` to measure coverage. Add this custom prop to the `doPlugins` function of your `AppMeasurement.js` or `s_code.js` files:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Step 6: Add Visitor API code to the page {#section-d46d6aa324c842f2931d901e38d6db1d}

Place the `VisitorAPI.js` file within the `<head>` tags on each page. Cuando coloque el archivo `VisitorAPI.js` en su página:

* Put it at the beginning of the `<head>` section to it appears before other solution tags.
* Debe ejecutarse antes de AppMeasurement y el código de otras soluciones de [!DNL Experience Cloud].

Mueva este código a producción después de la prueba y verificación.

## Step 7: (Optional) Configure a grace period {#section-7bbb2f72c26e4abeb8881e18366797a3}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). Los períodos de gracia pueden prolongarse hasta 180 días. Si es necesario, puede renovar un período de gracia.

**Implementación parcial**

Necesita un período de gracia si dispone de páginas que usan el servicio de ID y otras que no, y todas reportan al mismo grupo de informes de [!DNL Analytics]. Esta suele ser la situación habitual cuando se tiene un grupo de informes global que reporta entre dominios.

Interrumpa el período de gracia una vez que se haya implementado el servicio de ID en todas las páginas web que reportan al mismo grupo de informes.

**Requisitos de la cookie s_vi**

Necesita un período de gracia si necesita que nuevos visitantes tengan una cookie s_vi después de migrar al servicio de ID. Esto es lo habitual si su implementación lee la cookie s_vi y la almacena en una variable.

Interrumpa el período de gracia cuando su implementación pueda capturar el MID en lugar de leer la cookie s_vi.

Consulte [Cookies y el servicio Experience Cloud ID](../introduction/cookies.md).

Necesita un período de gracia si envía datos a un sistema interno desde una fuente de datos de flujo de navegación y si sus procesos utilizan las columnas `visid_high` y `visid_low`.

Discontinue the grace period after your data ingestion process can use the `post_visid_high` and `post_visid_low` columns.

Consulte [Referencia de columnas de datos del flujo de navegación](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

**Consumo de datos de flujo de navegación**

## Step 8: Test and deploy ID Service code {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Puede probar e implementar de la siguiente manera.

**Probar y verificar**

Para probar la implementación del servicio de ID, compruebe:

* la [cookie AMCV](../introduction/cookies.md) en el dominio en el que está alojada su página.
* El valor MID en la solicitud de imagen de [!DNL Analytics] con la [herramienta de depuración de Adobe](https://marketing.adobe.com/resources/help/en_US/sc/implement/debugger.html).

See, [Test and Verify the Experience Cloud ID Service](../implementation-guides/test-verify.md).

**Implementación de código**

Implementación del código una vez pasada la prueba.

Si ha habilitado un período de gracia en el [Paso 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Asegúrese de que el ID de [!DNL Analytics] (AID) y el MID estén en la solicitud de imagen.
* Recuerde deshabilitar el período de gracia cuando se cumplan los criterios para ello.
