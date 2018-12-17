# 加密解密插件，jsencrypt.js改良版用法：
var privaeKsy = 'MIICXAIBAAKBgQCsPfVw6icihqkmrAWEBi+3hBnYQc0lDx6WvG409LvW7cdI5/TM\n' +
    '5+K/myMlS7yT3vTawNZrpbT3JdhR/ubMHt+F7FOfr7q3uZ61Q3jQ99cyZaauZOMK\n' +
    'WjO/RkzNXT133f77+53UXo1uJ1D5AefS8q6a44mfv0tXIUJyj4IyX/6XrwIDAQAB\n' +
    'AoGAIrHES79OrLy1O83wunxIhk28qvvuJ6XZAoHoLRCS+aMhvkTC4bdfzDqipLOR\n' +
    'w7NoXNv1FO/m+NWNsk6HDNy3Jz0lqbmpkTzLOkRC/yWI200FofnEzmhASOW9kq0d\n' +
    'sWtB1+BNhHDsLYRU31wZZ8VZ9GgskDy3rLViiDBNlWB+NJECQQDYiFHuPWwRsv8O\n' +
    'E37vCICmDQo79hJrf2AdPmbftqFAfXc2FL96Ywwy8OzflFQReMTM9KeXza96FCRS\n' +
    '0p70SdmHAkEAy6L9QFlr4RSq37b5Zof5ImzsGSABjMxHng+xCoC4JpEbi5VI0Nay\n' +
    'Ewvo0imIZ/lRK3LjiNy1YbtV/0sv75U6mQJAPE6zawRGbiOJcBUz/EVE93qYSB0A\n' +
    'AlqmnV587oACJ2EKa9CZh+/APQvnHVpFk9wsC910NA6AeiLT/xFUXjuXTwJBAJWX\n' +
    '1pM/HZDrrdtKf0xi9xHjEk4ixQC50KK8xEIC7UTntGSF9kf0cDytswswl5RKAub4\n' +
    'L06LVHPHOxWgFkbaSYECQFEIQoSVC1+pB0XD5RhMp+Jo5KWBSBLhvoEEiJK+fRPR\n' +
    'NxwiKGppdp+kgxfxzEiO27sI42LkhztegWLh5HN0fc4=';

var publicKey = 'MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCsPfVw6icihqkmrAWEBi+3hBnY\n' +
    'Qc0lDx6WvG409LvW7cdI5/TM5+K/myMlS7yT3vTawNZrpbT3JdhR/ubMHt+F7FOf\n' +
    'r7q3uZ61Q3jQ99cyZaauZOMKWjO/RkzNXT133f77+53UXo1uJ1D5AefS8q6a44mf\n' +
    'v0tXIUJyj4IyX/6XrwIDAQAB';

// Create the encryption object and set the key.
var crypt = new JSEncrypt();
crypt.setKey(publicKey); //You can use also setPrivateKey and setPublicKey, they are both alias to setKey

//Eventhough the methods are called setPublicKey and setPrivateKey, remember
//that they are only alias to setKey, so you can pass them both a private or
//a public openssl key, just remember that setting a public key allows you to only encrypt.

var text = 'iiiiiiiiiiiiiiiiiiyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy';
// Encrypt the data with the public key.
var enc = crypt.encryptLong(text);
alert(enc);
crypt.setKey(privaeKsy);
// Now decrypt the crypted text with the private key.
var dec = crypt.decryptLong(enc);
alert(dec);
// Now a simple check to see if the round-trip worked.
if (dec === text){
    alert('It works!!!');
} else {
    alert('Something went wrong....');
}
