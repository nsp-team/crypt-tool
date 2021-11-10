[![Latest Stable Version](http://poser.pugx.org/nsp-team/crypt-tool/v)](https://packagist.org/packages/nsp-team/crypt-tool) 
[![Total Downloads](http://poser.pugx.org/nsp-team/crypt-tool/downloads)](https://packagist.org/packages/nsp-team/crypt-tool) 
[![Latest Unstable Version](http://poser.pugx.org/nsp-team/crypt-tool/v/unstable)](https://packagist.org/packages/nsp-team/crypt-tool) 
[![License](http://poser.pugx.org/nsp-team/crypt-tool/license)](https://packagist.org/packages/nsp-team/crypt-tool) 
[![PHP Version Require](http://poser.pugx.org/nsp-team/crypt-tool/require/php)](https://packagist.org/packages/nsp-team/crypt-tool)



# Summary

crypt包为phpseclib AES-128库创建了一个简单的接口。它的接口允许使用base64编码层对字符串进行加密和解密，以便于传输，包括初始化向量。.

# Installation

```bash
composer require nsp-team/crypt-tool:~1.0.0
```

# Usage

Before using the library, you need to choose a secret key, which should be of size 16, 24 or 32 only.

```php
<?php

use NspTeam\Crypt\Crypt;

$secretKey = "1234567890123456";

//1. Encrypt and Encode plain text data for storage or transmission 
$encodedEncryptedData = (new Crypt($secretKey))->encrypt("message");

//2. Decoding and Decrypting stored or received data
$encodedEncryptedData = (new Crypt($secretKey))->decrypt("encoded_encrypted_data");

//3. Encrypting and Decrypting with an alternate length initialization vector

$crypt = new Crypt($secretKey);

$alternateIVLength = 8;
$encodedEncryptedData = $crypt->encrypt("message", $alternateIVLength);
$plainText = $crypt->decrypt($encodedEncryptedData, $alternateIVLength);
```


When bad data is passed in, the return value of method call `CrowdStar\Crypt\Crypt::decrypt()` will be an empty string.

# PhpUnit
`php phpunit.phar --bootstrap tests/bootstrap.php  tests/CryptTest.php`
