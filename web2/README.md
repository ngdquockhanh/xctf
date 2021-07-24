# web2

![Screenshot from 2021-07-24 23-44-39](https://user-images.githubusercontent.com/87865134/126875355-3cb50698-516f-4014-aba7-eb61430047d6.png)

- **Hint:** write function decode `$miwen`
```php
function decode($str){
    $_o = base64_decode(strrev(str_rot13($str)));

    $_='';

    for($_0=0; $_0 < strlen($_o); $_0++){
        $_c=substr($_o,$_0,1); 
        $__=ord($_c)-1;
        $_c=chr($__);
        $_=$_.$_c;
    }

    return strrev($_);
}
```
- **Run function: `decode($miwen)` and got flag**
