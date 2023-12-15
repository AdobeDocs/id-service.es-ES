---
description: Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio de ID de Experience Cloud y no utilizan etiquetas de recopilación de datos. Sin embargo, recomendamos encarecidamente que utilice etiquetas para implementar el servicio de ID. Las etiquetas optimizan el flujo de trabajo de implementación y garantizan automáticamente la correcta ubicación y secuenciación del código.
keywords: Servicio de ID
title: Implementación del servicio de Experience Cloud ID para Target
exl-id: 7a387e98-c8fc-4904-942a-be5e527eada2
source-git-commit: 792fb5d5192843f345577a99b6179fb6d95fedc0
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 73%

---

# Implementación del servicio de Experience Cloud ID para Target{#implement-the-experience-cloud-id-service-for-target}

Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio de ID de Experience Cloud y no utilizan [Etiquetas de recopilación de datos](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=es). Sin embargo, recomendamos encarecidamente que utilice etiquetas para implementar el servicio de ID. Las etiquetas optimizan el flujo de trabajo de implementación y garantizan automáticamente la correcta ubicación y secuenciación del código.

>[!IMPORTANT]
>
>* [Lea los requisitos](../reference/requirements.md) antes de comenzar.
>* Configure y pruebe este código en un entorno de desarrollo antes de implementarlo en producción.

## Paso 1: Obtención del código del servicio de ID {#section-b32ba0548aa546a79dd38be59832a53e}

El [!UICONTROL servicio de ID] requiere la biblioteca de códigos `VisitorAPI.js`. Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) para obtener este código.

## Paso 2: Añadir la función Visitor.getInstance al código del servicio de ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: Copie la función Visitor.getInstance a continuación**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Parte 2: Añadir código de función al archivo VisitorAPI.js**

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

En la `Visitor.getInstance` función, sustituya `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` por su [!DNL Experience Cloud] ID de organización de. Si no conoce su ID de organización, puede encontrarlo en la página de administración de [!DNL Experience Cloud]. Consulte también [Administración - Servicios principales](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/admin-getting-started.html?lang=es). Su función editada podría tener un aspecto similar al ejemplo siguiente.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*Respete* las mayúsculas y minúsculas de su ID de organización. El ID distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

## Paso 4: Añadir el código de API de visitante a la página {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implemente el archivo `VisitorAPI.js` en su sitio en las etiquetas `<head>` antes de la referencia al archivo `mbox.js`. El servicio de ID de [!DNL Experience Cloud] debe ejecutarse para que pueda generarse la primera llamada de red de [!DNL Target]. Mueva este código a producción después de la prueba y verificación.

## Paso 5: Prueba e implementación del código de servicio de ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Puede realizar pruebas e implementaciones de la siguiente manera.

**Prueba y verificación**

Para probar la implementación del servicio de ID:

* Compruebe que cuenta con la cookie AMCV en el dominio en el que está alojada su página.
* Verifique que aparezca `mboxMCGVID` en su solicitud de [!DNL Target] y que contenga el ID de [!DNL Experience Cloud] (MID).

Consulte la información relativa a [Cookies y el servicio de Experience Cloud ID](../introduction/cookies.md) para obtener información sobre la cookie AMCV y el MID.

**Implementar**

Implemente el código después de pasar la prueba.
