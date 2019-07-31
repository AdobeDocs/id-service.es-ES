---
description: El servicio Experience Cloud ID (ECID) admite el algoritmo hash SHA -256 que le permite pasar ID de cliente o direcciones de correo electrónico y transferir ID hash. Es un método opcional Javascript para enviar identificadores hash a Experience Cloud. Puede seguir utilizando sus propios métodos de hash antes de enviar ID de clientes.
keywords: Servicio de ID
seo-description: El servicio Experience Cloud ID (ECID) admite el algoritmo hash SHA -256 que le permite pasar ID de cliente o direcciones de correo electrónico y transferir ID hash. Es un método opcional Javascript para enviar identificadores hash a Experience Cloud. Puede seguir utilizando sus propios métodos de hash antes de enviar ID de clientes.
seo-title: SHA 256 Hash Support for setcustomerids
title: SHA 256 Hash Support for setcustomerids
translation-type: tm+mt
source-git-commit: c670939cbeaebf4530df0e7d12e992ca5f0963bd

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

El servicio Experience Cloud ID (ECID) admite el algoritmo hash SHA -256 que le permite pasar ID de cliente o direcciones de correo electrónico y transferir ID hash. Es un método opcional Javascript para enviar identificadores hash a Experience Cloud. Puede seguir utilizando sus propios métodos de hash antes de enviar ID de clientes.
Existen dos maneras de implementar la compatibilidad hash con setcustomerids, tal como se describe en las secciones siguientes:

* Utilizar el método setcustomerids en ECID
* Agregar una acción en Adobe Experience Platform Launch

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

Antes de hash, la biblioteca ECID realiza normalización de datos en customerids. Este proceso recorta los espacios blancos de customerids en ambos extremos y convierte todos los caracteres a minúsculas. Por ejemplo, en las direcciones de correo electrónico: " ecid@adobe.com "se convierte en" ecid@adobe.com "

Consulte a continuación un ejemplo de código de cómo configurar un único ID de cliente (la dirección de correo electrónico mencionada anteriormente) con hash SHA -256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

Junto con el ID de visitante de Experience Cloud, puede asociar ID de cliente adicionales, estado de autenticación y tipo de hash (SHA -256) con cada visitante. Si no proporciona ningún tipo de hash, se considerará como sin hash.

El `setCustomerIDs` método acepta múltiples ID de cliente para el mismo visitante. Ayuda a identificar o dirigirse a un usuario individual entre distintos dispositivos. Por ejemplo, puede cargar estos ID como [atributos de cliente](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) a Experience Cloud y acceder a estos datos en las distintas soluciones.

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. Una llamada de ejemplo podría tener el aspecto siguiente. Se agregaron los saltos de línea para mayor claridad.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| Parámetro | Descripción |
|------------|----------|
| `d_cid_ic` | Pasa el código de integración, el ID de usuario único (DPUUID) y un ID de estado autenticado al servicio de ID. Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>Estado de autenticación</b> <br> Es un ID opcional en el parámetro d_ cid_ ic. Se expresa como un entero e identifica a los usuarios en función de su estado de autenticación, como se muestra a continuación: <br> <ul><li>0 (desconocido o nunca autenticado)</li><li>1 (actualmente autenticado para este contexto/página/contexto de aplicación)</li><li>2 (Desconectado)</li></ul> <br> Ejemplos: <br> <ul><li>Desconocido: ...d_cid=123%01456%01<b>0</b></li><li>Autenticado: ...d_cid=123%01456%01<b>1</b></li><li>Desconectado: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Launch Platform Launch es la nueva generación de funciones de administración de etiquetas de Adobe. Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

Tras confirmar la configuración, Launch ajusta los datos en un objeto, como se muestra a continuación:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

Este es un ejemplo de código:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.