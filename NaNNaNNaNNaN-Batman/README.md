# NaNNaNNaNNaN-Batman

### 1. Download the attachment, and open it
![Screenshot from 2021-07-26 01-55-05](https://user-images.githubusercontent.com/87865134/126910159-0dfbd3f6-3dcf-4740-ab6c-69c37f3ba933.png)
  - This is JS code in `<script>` tag
 
### 2. Change file to .hml and run it on browser
![Screenshot from 2021-07-26 01-56-36](https://user-images.githubusercontent.com/87865134/126910210-b39d3d04-a8e3-4d58-8b81-d0e1248882e5.png)
![Screenshot from 2021-07-26 01-57-18](https://user-images.githubusercontent.com/87865134/126910211-d308c4a7-23a2-4a78-a5f5-663d995a0950.png)

### 3. Change `eval(_)` to `alert(_)` to alert source code in browser
![Screenshot from 2021-07-26 02-46-39](https://user-images.githubusercontent.com/87865134/126911509-30f33fba-30f3-4ec0-a506-ba58bb3a4eb1.png)
  - **source code:** 
  ```JavaScript
  function $() {
        var e = document.getElementById("c").value;
        if (e.length == 16)
            if (e.match(/^be0f23/) != null)
                if (e.match(/233ac/) != null)
                    if (e.match(/e98aa$/) != null)
                        if (e.match(/c7be9/) != null) {
                            var t = ["fl", "s_a", "i", "e}"];
                            var n = ["a", "_h0l", "n"];
                            var r = ["g{", "e", "_0"];
                            var i = ["it'", "_", "n"];
                            var s = [t, n, r, i];
                            for (var o = 0; o < 13; ++o) {
                                document.write(s[o % 4][0]);
                                s[o % 4].splice(0, 1)
                            }
                        }
    }
    document.write('<input id="c"><button onclick=$()>Ok</button>');
    delete _
  ```
### 4. Run code in condition to get flag
  ```JavaScript
  var t = ["fl", "s_a", "i", "e}"];
  var n = ["a", "_h0l", "n"];
  var r = ["g{", "e", "_0"];
  var i = ["it'", "_", "n"];
  var s = [t, n, r, i];
  for (var o = 0; o < 13; ++o) {
    document.write(s[o % 4][0]);
    s[o % 4].splice(0, 1)
  }
  ```
![Screenshot from 2021-07-26 02-50-02](https://user-images.githubusercontent.com/87865134/126911618-ccb45b34-18b4-41bb-ae60-8afb4badc2a4.png)


