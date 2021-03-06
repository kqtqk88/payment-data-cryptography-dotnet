# Google Pay - payment data cryptography in C#

## Overview

.NET idiomatic library that performs the steps outlined in [Payment data cryptography](https://developers.google.com/pay/api/web/guides/resources/payment-data-cryptography).
It allows you to decrypt and verify a `PaymentMethodToken` object generated by
the Google Pay API. It supports versions `ECv1` and `ECv2`.

Internally, it relies on [Bouncy Castle C#](https://www.bouncycastle.org/csharp/index.html)
and has no other external dependencies.

## Sample use

```
// To use INSTANCE_TEST, set the parameter to true
var keyProvider = new GooglePay.PaymentDataCryptography.GoogleKeyProvider(false);
var parser = new GooglePay.PaymentDataCryptography.PaymentMethodTokenRecipient("merchant:YOUR_MERCHANT_ID", keyProvider);
parser.AddPrivateKey(PrivateKey1);
parser.AddPrivateKey(PrivateKey2);
string decryptedMessage = parser.Unseal(encryptedMessage);
```

## Disclaimer

This is not an official Google product.

[Tink](https://github.com/google/tink) is the library actively maintained and
supported by the Google Pay team. Using Tink to perform payment data
cryptography for Google Pay is highly recommended.
