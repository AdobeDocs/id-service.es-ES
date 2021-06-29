---
description: El servicio de Experience Cloud ID (ECID) es compatible con el algoritmo de hash SHA-256 que le permite pasar los ID de clientes o direcciones de correo electrónico, así como los ID de hash. Es un método opcional Javascript para enviar identificadores hash a Experience Cloud. Puede seguir utilizando sus propios métodos de hash antes de enviar ID de clientes.
keywords: Servicio de ID
title: Soporte hash SHA 256 para setCustomerIDs
exl-id: fd30634e-6435-4d14-8804-649c1ad3aaaa
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '606'
ht-degree: 100%

---

# Soporte hash SHA 256 para `setCustomerIDs` {#hashing-support}

El servicio de Experience Cloud ID (ECID) es compatible con el algoritmo de hash SHA-256 que le permite pasar los ID de clientes o direcciones de correo electrónico, así como los ID de hash. Es un método opcional Javascript para enviar identificadores hash a Experience Cloud. Puede seguir utilizando sus propios métodos de hash antes de enviar ID de clientes.
Existen dos maneras de implementar la compatibilidad hash con setCustomerIDs, tal como se describe en las secciones siguientes:

* [Utilizar el método setCustomerIDs en ECID](/help/reference/hashing-support.md#use-setcustomerids-method)
* [Añadir una acción en Adobe Experience Platform Launch](/help/reference/hashing-support.md#add-action-launch)

## Uso del método `setCustomerIDs` en ECID {#use-setcustomerids-method}

El primer método aprovecha el uso del método [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`).

Antes del hashing, la biblioteca ECID realiza la normalización de datos en customerIDs. Este proceso recorta los espacios en blanco de los customerIDs en ambos extremos y convierte todos los caracteres en minúsculas. Por ejemplo, en las direcciones de correo electrónico: &quot;ecid@adobe.com&quot; se convierte en &quot;ecid@adobe.com&quot;

Consulte a continuación un ejemplo de cómo configurar un único ID de cliente (la dirección de correo electrónico mencionada anteriormente) con hashing SHA -256.

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

Junto con el ID de visitante de Experience Cloud, se pueden asociar ID de cliente adicionales y un estado de autenticación a cada visitante. Si no proporciona ningún tipo de hash, se considerará como sin hash.

El `setCustomerIDs` método acepta múltiples ID de cliente para el mismo visitante. Ayuda a identificar o dirigirse a un usuario individual entre distintos dispositivos. Por ejemplo, puede cargar estos ID como [atributos de cliente](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=es) en Experience Cloud y acceder a estos datos en las distintas soluciones.

Los ID de cliente, los estados autenticados y el tipo de hash *no se* almacenan en una cookie que se utilizará después. En su lugar, los ID de cliente, los estados autenticados y el tipo de hash deben almacenarse en una variable de instancia para recuperarse usando [`getCustomerIDs`](/help/library/get-set/getcustomerids.md)como se muestra a continuación:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Los resultados del método `setCustomerIDs` dan como resultado una llamada al servicio Experience Cloud ID, un `dpm.demdex.net`, con la adición del parámetro de consulta `d_cid_ic`, que contiene el ID de cliente con hash. Una llamada de ejemplo podría parecerse a la de abajo. Se agregaron los saltos de línea para una mayor claridad.

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

Consulte la tabla siguiente para ver una descripción del parámetro`d_cid_ic` y del estado de autenticación.

| Parámetro | Descripción |
|------------|----------|
| `d_cid_ic` | Pasa el código de integración, el ID único de usuario (DPUUID) y un ID de estado autenticado al servicio de identidad. Separe el código de integración y el DPUUID con el carácter de control sin impresión, %01</code>: <br> Ejemplo: d_cid_ic = Integration_ code% 01DPUUID%01Authentication_state</code> <br> <b>Estado de autenticación</b> <br> Se trata de un ID opcional en el parámetro d_cid_ic. Se expresa como un entero e identifica a los usuarios en función de su estado de autenticación, como se muestra a continuación: <br> <ul><li>0 (Desconocido o nunca autenticado)</li><li>1 (Actualmente autenticado para esta instancia/página/contexto de aplicación)</li><li>2 (Desconectado)</li></ul> <br> Ejemplos: <br> <ul><li>Desconocido: ...d_cid=123%01456%01<b>0</b></li><li>Autenticado: ...d_cid=123%01456%01<b>1</b></li><li>Desconectado: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Añadir una acción en Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch es la función de administración de etiquetas de próxima generación de Adobe. Obtenga más información sobre Platform Launch en la [documentación del producto de Launch](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=es).

Para añadir una acción en Launch, lea la [documentación de reglas](https://docs.adobe.com/help/es-ES/launch/using/reference/manage-resources/rules.html) en Adobe Launch y vea la captura de pantalla a continuación:

![](/help/reference/assets/hashing-support.png)

<br> 

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

De manera similar al método `setCustomerIDs` descrito en la primera sección, esto resulta en una llamada al servicio Experience Cloud ID, con la adición del parámetro de consulta `d_cid_ic`.
