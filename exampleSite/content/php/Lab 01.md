+++
author = "Hugo Authors"
title = "Lab 01: Logic control"
date = "2020-09-25"
description = "Sample article showcasing basic Markdown syntax and formatting for HTML elements."
tags = [
    "PHP",
    "Redistering DN",
]
categories = [
    "PHP",
    "Lab 01",
    "logic control",
]
series = ["Themes Guide"]
aliases = ["migrate-from-jekyl"]
+++

DNS & Registering DN
<!--more-->

### 1. Giả Lập máy tính điện tử

##### Yêu cầu chức năng:  

![giả lập máy tính](../../images/calculator/Calculator-default.png)

- Máy tính phải thực hiện được tối thiểu các phép toán: +, -, *, /, %.  
- Nếu người dùng nhập đúng dữ liệu (nhập số và đúng phép toán), bấm vào nút “Xem  kết quả” thì xuất ra kết quả, đồng thời giữ lại số và phép toán trên các ô nhập liệu.  
- Nếu người dùng nhập sai (không phải là số, phép toán không tồn tại) thì thông báo  
không thực hiện được, và cho phép người dùng nhập lại.  
- Nếu người dùng bấm vào nút Xóa, thì xóa toàn bộ dữ liệu hiện có trên giao diện.



##### Giả lập với PHP + css
>Preview


![giả lập máy tính](../../images/calculator/final.png)


>khi nhập sai thì báo lỗi


![giả lập máy tính](../../images/calculator/bug.png)


>index.php
```html 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
<?php
            $n1 = "";
            $n2 = "";
            $calculate = "";
            $flag = true;
        
            if(isset($_POST["number1"]) && isset($_POST["calculate"]) && isset($_POST["number2"])){
                 $n1 = $_POST["number1"];
                 $n2 = $_POST["number2"];
                 $calculate = $_POST["calculate"];
            }

            if(is_numeric($n1) && is_numeric($n2)){
                switch ($calculate) {
                    case "+":
                    $result = $n1 + $n2;
                    break;
                    case "-":
                    $result = $n1 - $n2;
                    break;
                    case "*":
                    case "x":
                    $result = $n1 * $n2;
                    break;
                    case "/":
                    case ':':
                    $result = $n1 / $n2;
                    break;
                    case "%";
                    $result = $n1 % $n2;
                    break;
                    default:
                    $result = $n1 + $n2;
                    break;
                }
            }else{
                $result = "Bạn nhập sai, vui lòng nhập lại !";
                $flag = false;
            }
            
        ?>
        <div class="content">
            <h1>MÔ PHỎNG MÁY TÍNH</h1>
            <form action="#" method="POST" name="main-form">
                <div class="row">
                    <span>Số thứ nhất</span>
                    <input type="text" name="number1" value="<?php echo $n1;?>"/>
                </div>
                <div class="row">
                    <span>Phép toán</span>
                    <input type="text" name="calculate" value="<?php echo $calculate;?>"/>
                </div>
                <div class="row">
                    <span>Số thứ hai</span>
                    <input type="text" name="number2" value="<?php echo $n2;?>"/>
                </div>
                <div class="row">
                    <input type="submit" name="submit"/>
                </div>
                <div class="row">
                    <p>
                        <?php 
                            if($flag == true){
                                echo "Kết quả : " . $n1 ." ". $calculate ." ". $n2 ." = ". $result;
                            }
                            else{
                                echo $result;
                            }
                        ?>
                         </p>
                </div>
            </form>
        </div>
</body>
</html>
```

>styles.css
```css
body{
    margin: 0;
    padding: 0;
}
.content{
    margin: 20px auto;
    width: 600px;
    border: 1px solid #b1b1b1;
    padding: 10px;
}
.content h1 {
    color: firebrick;
    margin: auto;
    text-align: center;
}
.content div.row{
    margin-top: 20px;
}

.content div.row span{
    display: inline-block;
    width: 255px;
    text-align: right;
}

.content div.row input[type=text]{
    padding: 3px 5px;
}

.content div.row input[type=submit]{
    padding: 3px 5px;
    display: block;
    margin:  0px auto 20px auto;
}

.content div.row p{
    font-weight: bold;
    font-size: 20px;
    text-align: center;
}

```



##### Giả lập với HTML + CSS + JavaScript
>Preview


![giả lập máy tính](../../images/calculator/Cal2.png)

>index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./styles.css">
</head>
<body>
    <form id="calculator">
        <div class="top">
          <input class="screen" type="text" name="display" disabled>
        </div>
        <div class="key">
          <button class="button" type="button" value="1" onclick="calculator.display.value += 1">1</button>
          <button class="button" type="button" value="2" onclick="calculator.display.value += 2">2</button>
          <button class="button" type="button" value="3" onclick="calculator.display.value += 3">3</button>
          <button class="eval" type="button" value="+" onclick="calculator.display.value += '+'">+</button>
        </br>
          <button class="button" type="button" value="4" onclick="calculator.display.value += 4">4</button>
          <button class="button" type="button" value="5" onclick="calculator.display.value += 5">5</button>
          <button class="button" type="button" value="6" onclick="calculator.display.value += 6">6</button>
          <button class="eval" type="button" value="-" onclick="calculator.display.value += '-'">-</button>
        </br>
          <button class="button" type="button" value="7" onclick="calculator.display.value += 7">7</button>  
          <button class="button" type="button" value="8" onclick="calculator.display.value += 8">8</button>
          <button class="button" type="button" value="9" onclick="calculator.display.value += 9">9</button>
          <button class="eval" type="button" value="x" onclick="calculator.display.value += '*'">x</button>
        </br>
          <button class="clear" type="button" id="clear" name="clear" value="C" onclick="calculator.display.value = ''">c</button>
          <button class="button" type="button" name="zero" value="0" onclick="calculator.display.value += '0'">0</button>
          <button class="button" type="button" name="doit" value="=" onclick="calculator.display.value = eval(calculator.display.value)">=</button>
          <button class="eval" type="button" name="div" value="/" onclick="calculator.display.value += '/'">/</button>
        </div>  
      </form>
</body>
</html>
```

>styles.css

```css
/* Basic reset */
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font: bold 14px Arial, sans-serif;
}

html {
	height: 100%;
	background: white;
	background: radial-gradient(circle, #fff 20%, #ccc);
	background-size: cover;
}

#calculator {
	width: 340px;
	height: 260px;
	margin: 100px auto;
	padding: 20px 20px 9px;
	background: #9dd2ea;
	background: linear-gradient(#9dd2ea, #8bceec);
	border-radius: 3px;
	box-shadow: 0px 4px #009de4, 0px 10px 15px rgba(0, 0, 0, 0.2);
}

.top .clear {
	float: left;
}

.top .screen {
	height: 40px;
	width: 100%;
	padding: 0 10px;
	background: rgba(0, 0, 0, 0.2);
	border-radius: 3px;
	box-shadow: inset 0px 4px rgba(0, 0, 0, 0.2);
	font-size: 17px;
	line-height: 40px;
	color: white;
	text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
	text-align: right;
	letter-spacing: 1px;
}

.key{
	padding-top: 10px;
	padding-left: 6px;
}

.keys, .top {overflow: hidden;}

.button {
	float: left;
	position: relative;
	border: 0;
	width: 66px;
	height: 36px;
	background: white;
	border-radius: 3px;
	box-shadow: 0px 4px rgba(0, 0, 0, 0.2);
	margin: 0 7px 11px 0;
	color: #888;
	line-height: 36px;
	text-align: center;
}

.eval {
	float: left;
	position: relative;
	border: 0;
	width: 66px;
	height: 36px;
	border-radius: 3px;
	box-shadow: 0px 4px rgba(0, 0, 0, 0.2);
	margin: 0 7px 11px 0;
	color: white;
	line-height: 36px;
	text-align: center;
	background: #f1ff92;
	color: #888e5f;
}

.clear{
	float: left;
	position: relative;
	border: 0;
	width: 66px;
	height: 36px;
	background: #faaeb3;
	border-radius: 3px;
	box-shadow: 0px 4px rgba(0, 0, 0, 0.2);
	margin: 0 7px 11px 0;
	color: #888e5f;
	line-height: 36px;
	text-align: center;
}

.button:hover {
	background: #9c89f6;
	box-shadow: 0px 4px #6b54d3;
	color: white;
}

.eval:hover {
	background: #abb850;
	box-shadow: 0px 4px #717a33;
	color: #ffffff;
}

.clear:hover {
	background: #f68991;
	box-shadow: 0px 4px #d3545d;
	color: white;
}

.button:active {
	box-shadow: 0px 0px #6b54d3;
	top: 4px;
}

.eval:active {
	box-shadow: 0px 0px #717a33;
	top: 4px;
}

.clear:active {
	top: 4px;
	box-shadow: 0px 0px #d3545d;
}

```



### 2. Viết chương trình “cho biết bạn thuộc chòm sao nào, dựa vào ngày/tháng sinh”. Với giao  diện như sau:

![chòm sao](../../images/zodiac/ex.png)
##### Yêu cầu chức năng:  
- Cho người dùng nhập ngày + tháng sinh  
- Nếu ngày, tháng sinh hợp lệ, khi người dùng bấm vào nút “Lấy chòm sao!” thì hiển  thị: hình, cung hoàng đạo (tên chòm sao) và ngày tháng của cung hoàng đạo đó.   Nếu người dùng nhập dữ liệu không hợp lệ thì thông báo “Dữ liệu không hợp lệ”.   Nếu người dùng bấm vào nút “Xóa” thì xóa hết dữ liệu trên giao diện.  Danh sách các chòm sao:  
- Chòm sao ARIES – DƯƠNG CƯU sinh từ ngày 21/3 – 20/4  
- Chòm sao TAURUS – KIM NGƯU sinh từ ngày 21/4 – 21/5  
- Chòm sao GEMINI – SONG TỬ sinh từ ngày 22/5 – 21/6  
- Chòm sao CANCER – CỰ GIẢI sinh từ ngày 22/6-23/7  
- Chòm sao LEO – HẢI SƯ sinh từ ngày 24/7 – 23/8  
- Chòm sao VIRGO – XỬ NỬ sinh từ ngày 24/8 – 23/9  
- Chòm sao LIBRA – THIÊN XỨNG sinh từ ngày 24/9 – 23/10  
- Chòm sao SCORPIO – HỔ CÁP sinh từ ngày 24/10 – 22/11  
- Chòm sao SAGITTARIUS – NH N MÃ sinh từ ngày 23/11 – 21/12  
- Chòm sao CAPRICORNUS – MA KẾT sinh từ ngày 22/12 – 20/1  
- Chòm sao AQUARIUS – BẢO BÌNH sinh từ ngày 21/1 – 19/2  
- Chòm sao PISCES – SONG NGƯ sinh từ ngày 20/2 – 20/3  

