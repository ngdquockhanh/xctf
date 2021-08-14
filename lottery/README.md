# lottery
![Screenshot from 2021-08-14 16-51-12](https://user-images.githubusercontent.com/87865134/129442199-0f834905-9966-4ccd-a838-9da0c8e0c2d5.png)
![Screenshot from 2021-08-14 16-51-28](https://user-images.githubusercontent.com/87865134/129442200-85563c53-fa22-4df4-a8fa-f01a535134fa.png)
![Screenshot from 2021-08-14 17-01-30](https://user-images.githubusercontent.com/87865134/129442450-067130ab-2ae5-4ac4-af5c-76bcabc574d3.png)
![Screenshot from 2021-08-14 16-51-45](https://user-images.githubusercontent.com/87865134/129442203-3c1c40e2-650c-4abe-b634-47758ef117bd.png)

## - Hint: 
 - use $9990000 to by flag
 - source code in attachments:   
 ![Screenshot from 2021-08-14 16-55-07](https://user-images.githubusercontent.com/87865134/129442268-6970bc52-0e8d-4af2-a4d0-3f2952375b25.png)

## - View source code
- we find function `buy()` is vulnerable
```php
function buy($req){
	require_registered();
	require_min_money(2);

	$money = $_SESSION['money'];
	$numbers = $req['numbers'];
	$win_numbers = random_win_nums();
	$same_count = 0;
	for($i=0; $i<7; $i++){
		if($numbers[$i] == $win_numbers[$i]){
			$same_count++;
		}
	}
	switch ($same_count) {
		case 2:
			$prize = 5;
			break;
		case 3:
			$prize = 20;
			break;
		case 4:
			$prize = 300;
			break;
		case 5:
			$prize = 1800;
			break;
		case 6:
			$prize = 200000;
			break;
		case 7:
			$prize = 5000000;
			break;
		default:
			$prize = 0;
			break;
	}
	$money += $prize - 2;
	$_SESSION['money'] = $money;
	response(['status'=>'ok','numbers'=>$numbers, 'win_numbers'=>$win_numbers, 'money'=>$money, 'prize'=>$prize]);
}
```
-  `$numbers[$i] == $win_numbers[$i]` is vulnerable because it is a **Loose Comparison** in `PHP`
-  We can bypass using other data type
![Screenshot from 2021-08-14 17-00-54](https://user-images.githubusercontent.com/87865134/129442437-9a059fd1-6ee9-45a9-aee8-75c01adc847a.png)

## - Exploit:
- use **Burp Sutie** to intercept request
![Screenshot from 2021-08-14 17-03-57](https://user-images.githubusercontent.com/87865134/129442511-8f33113d-1010-4b93-b6b6-bdc843923967.png)
- change **number** in header and send request
```JSON
"numbers":[true, true, true, true, true, true, true]
```
![Screenshot from 2021-08-14 17-07-19](https://user-images.githubusercontent.com/87865134/129442615-c0c8eea9-1c18-43cf-be77-aab70a005ca5.png)
- Buy Flag
![Screenshot from 2021-08-14 17-09-24](https://user-images.githubusercontent.com/87865134/129442631-20f82d32-5c61-4051-a39b-1734a63019b9.png)


## - Reference
  - https://www.php.net/manual/en/types.comparisons.php
