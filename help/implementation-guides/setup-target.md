---
description: Estas instrucciones están destinadas a los clientes de Target que deseen utilizar el servicio Experience Cloud ID y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
keywords: Servicio de ID
seo-description: Estas instrucciones están destinadas a los clientes de Target que deseen utilizar el servicio Experience Cloud ID y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
seo-title: Implementación del servicio Experience Cloud ID para Target
title: Implementación del servicio Experience Cloud ID para Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Implementación del servicio Experience Cloud ID para Target{#implement-the-experience-cloud-id-service-for-target}

Estas instrucciones están destinadas a los clientes de Target que deseen utilizar el servicio Experience Cloud ID y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.

>[!IMPORTANT]
>
>* [Lea los requisitos](../reference/requirements.md) antes de comenzar.
>* Configure y pruebe este código en un entorno de desarrollo antes de implementarlo en producción.
>



## Step 1: Get the ID Service code {#section-b32ba0548aa546a79dd38be59832a53e}

[!DNL ID Service] La biblioteca de `VisitorAPI.js` código requiere. Contacte con el [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html) para obtener este código.

## Step 2: Add the Visitor.getInstance function to the ID Service code {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: Copia de la función Visitor.getInstance a continuación**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
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
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Step 3: Add your Experience Cloud Organization ID to Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

In the `Visitor.getInstance` function, replace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` with your [!DNL Experience Cloud] organization ID. Si no conoce su ID de organización, puede encontrarlo en la página de administración de [!DNL Experience Cloud]. Consulte también [Administración - Servicios principales](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). Su función editada podría tener un aspecto similar al ejemplo siguiente.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*No* cambie el caso de los caracteres del identificador de organización. El ID distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

## Step 4: Add Visitor API code to the page {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Deploy the `VisitorAPI.js` file to your site in the `<head>` tags before the reference to the `mbox.js` file. The [!DNL Experience Cloud] ID service must execute before the first [!DNL Target] network call is generated. Mueva este código a producción después de la prueba y verificación.

## Step 5: Test and deploy ID Service code {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Puede probar e implementar de la siguiente manera.

**Probar y verificar**

Para probar la implementación de su servicio de ID:

* Compruebe la cookie AMCV en el dominio en el que está alojada su página.
* Verify `mboxMCGVID` appears in your [!DNL Target] request and that it contains the [!DNL Experience Cloud] ID (MID).

See [Cookies and the Experience Cloud ID Service](../introduction/cookies.md) for information about the AMCV cookie and the MID.

**Implementación**

Implementación del código una vez pasada la prueba.
