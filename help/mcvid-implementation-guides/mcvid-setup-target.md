---
description: Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
keywords: Servicio de ID
seo-description: Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
seo-title: Implementación del servicio Experience Cloud ID para Target
title: Implementación del servicio Experience Cloud ID para Target
uuid: cb3581fa-4c4b-43aa-bb8e-8db85a6a1ef2
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Implementación del servicio Experience Cloud ID para Target{#implement-the-experience-cloud-id-service-for-target}

Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.

>[!IMPORTANT]
>
>* [Lea los requisitos](../mcvid-reference/mcvid-requirements.md) antes de comenzar.
>* Configure y pruebe este código en un entorno de desarrollo antes de implementarlo en producción.
>



## Paso 1: Obtención del código de servicio de ID {#section-b32ba0548aa546a79dd38be59832a53e}

El [!DNL ID Service] requiere la `VisitorAPI.js` biblioteca de código. Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) para obtener este código.

## Paso 2: Añadir la función Visitor.getInstance al código del servicio de ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: Copia de la función Visitor.getInstance a continuación**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Parte 2: Adición del código de función al archivo VisitorAPI.js**

Coloque la `Visitor.getInstance` función al final del archivo, después del bloque de códigos. El archivo editado debería tener un aspecto similar a este:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Paso 3: Añadir su ID de organización de Experience Cloud a Visitor.getInstance {#section-522b1877be9243c39b222859b821f0ce}

En la `Visitor.getInstance` función, sustituya `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` por su [!DNL Experience Cloud] ID de organización de. Si no conoce su ID de organización, puede encontrarlo en la página de [!DNL Experience Cloud]administración de. Consulte también [Administración - Servicios principales](https://marketing.adobe.com/resources/help/es_ES/mcloud/admin_getting_started.html). Su función editada podría tener un aspecto similar al ejemplo siguiente.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Respete* las mayúsculas y minúsculas de su ID de organización. El ID distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

## Paso 4: Añadir el código de API de visitante a la página {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implemente el archivo `VisitorAPI.js` en su sitio en las etiquetas `<head>` antes de la referencia al archivo `mbox.js`. El servicio de ID de [!DNL Experience Cloud] debe ejecutarse para que pueda generarse la primera llamada de red de [!DNL Target]. Mueva este código a producción después de la prueba y verificación.

## Paso 5: Prueba e implementación del código de servicio de ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Puede realizar pruebas e implementaciones de la siguiente manera.

**Prueba y verificación**

Para probar la implementación de su servicio de ID:

* Compruebe la cookie AMCV en el dominio en el que está alojada su página.
* Verifique que aparezca `mboxMCGVID` en su solicitud de [!DNL Target] y que contenga el ID de [!DNL Experience Cloud] (MID).

Consulte la información relativa a [Cookies y el servicio Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md) para obtener información sobre la cookie AMCV y el MID.

**Implementación**

Implementación del código una vez pasada la prueba.
