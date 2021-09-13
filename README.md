# node-onlykey

Get a Onlykey USB: [https://onlykey.io/sea](https://onlykey.io/sea)

Live Demo for 3rd Party: [https://trustcrypto.github.io/node-onlykey/docs/](https://trustcrypto.github.io/node-onlykey/docs/)

------

3rd Party Support
---

Supports
* ECDH and ECDSA (NIST256P1)
* ECDH and EDDSA (ED25519)
* NACL


API
----

```js
require("./dist/onlykey3rd-party.js")(function(ONLYKEY) {

  var ok = ONLYKEY();

})
```


Events
-----

```js
ok.on(event,function() {})
```

List of events

* `"status"`  outputs current operation in english
* `"error"`   emits any errors during operations
* `"debug"`   outpus any debug and status in english, _like `status` but more details_


Methods
-----

```js
ok.connect(function() {})
```
_connect does ECDH for secure session using NACL and informs hardware of current time, OS, and browser.


```js
ok.derive_public_key(AdditionalData, keyType, press_required, function(error, jwk_epub) {})
```

_derive_public_key does _connect and returns a hardware generated public key from OnlyKey

```
ok.derive_shared_secret(AdditionalData, jwk_epub, keyType, press_required, function(error, shared_secret) {})
```

_derive_public_key does _connect and returns a hardware generated shared secret from OnlyKey that can be used as private key for encryption/signing

*   `additional_d` = `string` or `buffer` to point to a derived key
*   `jwk_epub` = public key in jwk format
*   `keyType` = key generation type
*   `shared_secret`  = shared AES-GCM key

`KEYTYPE`
*   KEYTYPE_NACL = `0`
*   KEYTYPE_P256R1 = `1`
*   KEYTYPE_P256K1 = `2`
*   KEYTYPE_CURVE25519 = `3`


API Authors
-----------
* Tim ~  onlykey.io
* Brad ~  bmatusiak.us
