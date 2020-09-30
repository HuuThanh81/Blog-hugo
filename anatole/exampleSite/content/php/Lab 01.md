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


>index.php


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, maximum-scale=1.0, initial-scale=1.0, user-scalable=no">
    <title>Zodiac-sign | Hữu Thành</title>
    <link rel="stylesheet" href="./styles.css">

</head>
<body>
    <?php
        $Date="";
        $Month="";
        $Image="";
        $Name="";
        $Time="";
        $About="";
        $flag = true;
        $oops = true;

        if(isset($_POST["date"]) && isset($_POST["month"])){
                $Date = $_POST["date"];
                $Month = $_POST["month"];
        }

        if(is_numeric($Date) && is_numeric($Month)){
  
            switch ($Month){
                case 1:
                    if($Date <= 20){$Image = "capricorn"; $Name = "CAPRICORNUS"; $Time = "(22/12 – 20/1)"; $About = "CAPRICORN IS THE SIGN OF TRADITION, PERSEVERANCE AND LIFE’S WINTRY TIMES.

                        <br/>
                        You show power when you’re:
                        <br/>
                        committed to life’s work that’s deeply rewarding
                        exerting personal authority
                        feeling respected in your field or community
                        working toward mastery of skills
                        patience with your steady progress
                        compassionate toward your own melancholic feelings
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        all work and no play
                        unable to connect to wonder or mystery
                        too focused on status, convention
                        ruthless in attaining what you want
                        self-denigrating when you don’t meet your own high standards";}
                    if($Date >= 21){$Image = "aquarius"; $Name = "AQUARIUS"; $Time = "(21/1 – 19/2)"; $About = "AQUARIUS IS THE SIGN OF FAR-SIGHTEDNESS AND HUMANE VALUES.

                        <br/>
                        You show power when you’re:
                        <br/>
                        experimenting and following your path wherever it leads
                        daring in your thinking
                        able to think for the group, and see the big picture
                        open to breakthroughs that take you to the next level
                        friendly toward everyone equally
                        not afraid to be considered strange
                        <br/>
                        You lose power when you’re:
                        <br/>
                        stuck in an unusual, but rigid matrix of thought
                        defiant in a way that’s self-destructive
                        unable to create any kind of stability";}
                    if($Date <1 || $Date >31){$flag = false;}
                break;
                case 2:
                    if($Date <= 19){$Image = "aquarius"; $Name = "AQUARIUS"; $Time = "(21/1 – 19/2)"; $About = "AQUARIUS IS THE SIGN OF FAR-SIGHTEDNESS AND HUMANE VALUES.

                        <br/>
                        You show power when you’re:
                        <br/>
                        experimenting and following your path wherever it leads
                        daring in your thinking
                        able to think for the group, and see the big picture
                        open to breakthroughs that take you to the next level
                        friendly toward everyone equally
                        not afraid to be considered strange
                        <br/>
                        You lose power when you’re:
                        <br/>
                        stuck in an unusual, but rigid matrix of thought
                        defiant in a way that’s self-destructive
                        unable to create any kind of stability";}
                    if($Date >= 20){$Image = "pisces"; $Name = "PISCES"; $Time = "(20/2 – 20/3)"; $About = "PISCES IS THE SIGN OF HEIGHTENED SENSITIVITY AND IMAGINATION.

                        <br/>
                        You show power when you’re:
                        <br/>
                        able to release old wounds, and transform miraculously
                        using the power of your imagination
                        tuned into dreams and the spirit realms
                        grounded in a spiritual practice
                        honing your awareness of the subtle intuitive senses
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        absorbing too much of the energies around you
                        overwhelmed, without the time you need to process emotions
                        too involved in saving others, without tending to your own needs
                        losing your moral center because of the need to please
                        overexposed to stimulation, and unable to access the subtle senses";}
                    if($Date <1 || $Date >29){$flag = false;}
                break;
                case 3:
                    if($Date <= 20){$Image = "pisces"; $Name = "PISCES"; $Time = "(20/2 – 20/3)"; $About = "PISCES IS THE SIGN OF HEIGHTENED SENSITIVITY AND IMAGINATION.

                        <br/>
                        You show power when you’re:
                        <br/>
                        able to release old wounds, and transform miraculously
                        using the power of your imagination
                        tuned into dreams and the spirit realms
                        grounded in a spiritual practice
                        honing your awareness of the subtle intuitive senses
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        absorbing too much of the energies around you
                        overwhelmed, without the time you need to process emotions
                        too involved in saving others, without tending to your own needs
                        losing your moral center because of the need to please
                        overexposed to stimulation, and unable to access the subtle senses";}
                    if($Date >= 21){$Image = "aries"; $Name = "ARIES"; $Time = "(21/3 – 20/4)"; $About = "ARIES, YOURS IS A SIGN OF BLASTING FORTH ACTION.
                        <br/>
                        You show power when you’re:
                        <br/>
                        forceful
                        truthfully You
                        provocative
                        active and progressive
                        aggressive or competitive
                        confrontational when necessary
                        honest
                        optimistic
                        confident
                        fun-loving
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        stagnant and without the right creative outlets
                        antagonistic toward others
                        unable to read emotional subtleties
                        pushy when a light touch will do
                        always fired up, without downtime
                        burnt-out and emotionally brittle
                        fighting meaningless battles.";}
                    if($Date <1 || $Date >31){$flag = false;}
                break;
                case 4:
                    if($Date <= 20){$Image = "aries"; $Name = "ARIES"; $Time = "(21/3 – 20/4)"; $About = "ARIES, YOURS IS A SIGN OF BLASTING FORTH ACTION.
                        <br/>
                        You show power when you’re:
                        <br/>
                        forceful
                        truthfully You
                        provocative
                        active and progressive
                        aggressive or competitive
                        confrontational when necessary
                        honest
                        optimistic
                        confident
                        fun-loving
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        stagnant and without the right creative outlets
                        antagonistic toward others
                        unable to read emotional subtleties
                        pushy when a light touch will do
                        always fired up, without downtime
                        burnt-out and emotionally brittle
                        fighting meaningless battles.";}
                    if($Date >= 21){$Image = "taurus"; $Name = "TAURUS"; $Time = "(21/4 – 21/5)"; $About = "TAURUS IS A SIGN OF THRIVING AND STABILITY.
                        <br/>
                        You show power when you’re:
                        <br/>
                        steady-natured and thorough
                        deeply engaged in a satisfying discipline
                        actively enjoying sensual pleasures
                        creating abundance from your own natural talents
                        strong of body, mind, and spirit
                        rooted in a sense of place
                        tending to life in all its stages of growth
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        stubbornly resistant to change
                        weighed down by your possessions
                        unable to jump on opportunities
                        overindulgent, lazy or dull-minded
                        too set in your ways";}
                    if($Date <1 || $Date >30){$flag = false;}
                break;
                case 5:
                    if($Date <= 21){$Image = "taurus"; $Name = "TAURUS"; $Time = "(21/4 – 21/5)"; $About = "TAURUS IS A SIGN OF THRIVING AND STABILITY.
                        <br/>
                        You show power when you’re:
                        <br/>
                        steady-natured and thorough
                        deeply engaged in a satisfying discipline
                        actively enjoying sensual pleasures
                        creating abundance from your own natural talents
                        strong of body, mind, and spirit
                        rooted in a sense of place
                        tending to life in all its stages of growth
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        stubbornly resistant to change
                        weighed down by your possessions
                        unable to jump on opportunities
                        overindulgent, lazy or dull-minded
                        too set in your ways";}
                    if($Date >= 22){$Image = "gemini"; $Name = "GEMINI"; $Time = "(22/5 – 21/6)"; $About = "GEMINI IS THE SIGN OF FLUENCY AND NIMBLE CHANGE.
                        <br/>
                        You show power when you’re:
                        <br/>
                        mentally flexible
                        enlightening the scene with your intelligent humor
                        engaged in the dynamic whirl of life
                        learning something new
                        following a fascination
                        satisfying your curiosity
                        exploring your many sides
                        acknowledging your need for rest, along with motion
                        with stimulating friends or colleagues
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        too tightly wound
                        repeating things you know you shouldn’t
                        putting negativity into the collective stream
                        unable to sustain interest long enough to bring an idea to fruition
                        giving in to cynicism
                        not getting enough “Me” time to center yourself
                        not allowing for silence to hear your own thoughts";}
                    if($Date <1 || $Date >31){$flag = false;}
                break;
                case 6:
                    if($Date <= 21){$Image = "gemini"; $Name = "GEMINI"; $Time = "(22/5 – 21/6)"; $About = "GEMINI IS THE SIGN OF FLUENCY AND NIMBLE CHANGE.
                        <br/>
                        You show power when you’re:
                        <br/>
                        mentally flexible
                        enlightening the scene with your intelligent humor
                        engaged in the dynamic whirl of life
                        learning something new
                        following a fascination
                        satisfying your curiosity
                        exploring your many sides
                        acknowledging your need for rest, along with motion
                        with stimulating friends or colleagues
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        too tightly wound
                        repeating things you know you shouldn’t
                        putting negativity into the collective stream
                        unable to sustain interest long enough to bring an idea to fruition
                        giving in to cynicism
                        not getting enough “Me” time to center yourself
                        not allowing for silence to hear your own thoughts";}
                    if($Date >= 22){$Image = "cancer"; $Name = "CANCER"; $Time = "(22/6 – 23/7)"; $About = "CANCER IS THE SIGN OF EMOTIONS AND THE HOME.
                        <br/>
                        You show power when you’re:
                        <br/>
                        protecting the vulnerable
                        reading the emotional reality of any situation
                        drawing from your imagination
                        able to be yourself in a safe, familiar setting
                        create a homey atmosphere wherever you are
                        intuiting what’s going on, and acting on that information
                        being the keeper of memories, impressions, intimate stories
                        reclusive and fearful of being hurt
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        always on the defense
                        wounded and lashing out
                        only loving toward those in your clan (family, race, nation)
                        unable to see beyond your own problems";}
                    if($Date <1 || $Date >30){$flag = false;}
                break;
                case 7:
                    if($Date <= 23){$Image = "cancer"; $Name = "CANCER"; $Time = "(22/6 – 23/7)"; $About = "CANCER IS THE SIGN OF EMOTIONS AND THE HOME.
                        <br/>
                        You show power when you’re:
                        <br/>
                        protecting the vulnerable
                        reading the emotional reality of any situation
                        drawing from your imagination
                        able to be yourself in a safe, familiar setting
                        create a homey atmosphere wherever you are
                        intuiting what’s going on, and acting on that information
                        being the keeper of memories, impressions, intimate stories
                        reclusive and fearful of being hurt
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        always on the defense
                        wounded and lashing out
                        only loving toward those in your clan (family, race, nation)
                        unable to see beyond your own problems";}
                    if($Date >= 24){$Image = "leo"; $Name = "LEO"; $Time = "(24/7 – 23/8)"; $About = "LEO IS THE SIGN OF EXUBERANT CREATIVITY.
                        <br/>

                        You show power when you’re:
                        <br/>
                        larger-than-life with personality
                        dignified and full of self-respect
                        big-hearted, generous, a loyal friend
                        confidently leading and encouraging others
                        expressing the joy of being alive through all kinds of interests just-for-the-fun-of-it
                        matching the exuberance of children
                        exploring the drama of life through the arts, music, theater, etc
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        full of empty boasts
                        constantly in need of attention
                        demanding of special treatment
                        inconsiderate toward other people’s time, efforts, gifts
                        resentful from feeling disrespected
                        taking life too seriously";}
                    if($Date <1 || $Date >31){$flag = false;}
                break;
                case 8:
                    if($Date <= 23){$Image = "leo"; $Name = "LEO"; $Time = "(24/7 – 23/8)"; $About = "LEO IS THE SIGN OF EXUBERANT CREATIVITY.
                        <br/>

                        You show power when you’re:
                        <br/>
                        larger-than-life with personality
                        dignified and full of self-respect
                        big-hearted, generous, a loyal friend
                        confidently leading and encouraging others
                        expressing the joy of being alive through all kinds of interests just-for-the-fun-of-it
                        matching the exuberance of children
                        exploring the drama of life through the arts, music, theater, etc
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        full of empty boasts
                        constantly in need of attention
                        demanding of special treatment
                        inconsiderate toward other people’s time, efforts, gifts
                        resentful from feeling disrespected
                        taking life too seriously";}
                    if($Date >= 24){$Image = "virgo"; $Name = "VIRGO"; $Time = "(24/8 – 23/9)"; $About = "VIRGO IS THE SIGN OF DEVOTION, HEALTHY LIVING AND SELF-IMPROVEMENT.
                        <br/>

                        You show power when you’re:
                        <br/>
                        productive and working toward tangible goals
                        tuned into your body and its ability to heal, transform
                        being of service, in a way that enriching you also
                        analyzing systems and processes
                        offering your discerning perspective
                        sharing your gifts as a healer
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        too humble and don’t take credit for your accomplishments
                        always dissatisfied with where you are
                        paralyzed from self-criticism
                        spinning out on the little things that can go wrong
                        worry over all there is to do
                        overly fixated on your aches and pains";}
                    if($Date <1 || $Date >31){$flag = false;}
                break;
                case 9:
                    if($Date <= 23){$Image = "virgo"; $Name = "VIRGO"; $Time = "(24/8 – 23/9)"; $About = "VIRGO IS THE SIGN OF DEVOTION, HEALTHY LIVING AND SELF-IMPROVEMENT.
                        <br/>

                        You show power when you’re:
                        <br/>
                        productive and working toward tangible goals
                        tuned into your body and its ability to heal, transform
                        being of service, in a way that enriching you also
                        analyzing systems and processes
                        offering your discerning perspective
                        sharing your gifts as a healer
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        too humble and don’t take credit for your accomplishments
                        always dissatisfied with where you are
                        paralyzed from self-criticism
                        spinning out on the little things that can go wrong
                        worry over all there is to do
                        overly fixated on your aches and pains";}
                    if($Date >= 24){$Image = "libra"; $Name = "LIBRA"; $Time = "(24/9 – 23/10)"; $About = "LIBRA IS THE SIGN OF BEAUTY AND ART, AND ROMANTIC LOVE.

                        <br/>
                        You show power when you’re:
                        <br/>
                        a harmonizing influence
                        playing off another’s energies in a masterful way
                        modeling fairness
                        thriving in relationship
                        creating beauty
                        being stylish, graceful, elegant
                        advocating justice
                        restoring balance
                        being a peacemaker
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        being who you think another needs/wants you to be
                        fearful of direct action
                        avoiding a necessary confrontation
                        unwilling to see the dark, along with the light
                        full of great ideas, that never get executed";}
                    if($Date <1 || $Date >30){$flag = false;}
                break;
                case 10:
                    if($Date <= 23){$Image = "libra"; $Name = "LIBRA"; $Time = "(24/9 – 23/10)"; $About = "LIBRA IS THE SIGN OF BEAUTY AND ART, AND ROMANTIC LOVE.

                        <br/>
                        You show power when you’re:
                        <br/>
                        a harmonizing influence
                        playing off another’s energies in a masterful way
                        modeling fairness
                        thriving in relationship
                        creating beauty
                        being stylish, graceful, elegant
                        advocating justice
                        restoring balance
                        being a peacemaker
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        being who you think another needs/wants you to be
                        fearful of direct action
                        avoiding a necessary confrontation
                        unwilling to see the dark, along with the light
                        full of great ideas, that never get executed";}
                    if($Date >= 24){$Image = "scorpio"; $Name = "SCORPIO"; $Time = "(24/10 – 22/11)"; $About = "SCORPIO IS THE SIGN OF SEXUALITY, THE SHADOWS, AND GREAT FEATS.
                        <br/>

                        You show power when you’re:
                        <br/>
                        exploring the rich, shadowy terrain of the psyche
                        administering strong medicine in a way that has integrity
                        engaged in life’s work that’s totally absorbing
                        aware of your power to heal and transform
                        patiently strategic when waiting for the right time
                        extending yourself to go into someone else’s darkness, for healing
                        soulful
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        heavy with unresolved emotions and dramas
                        stuck in the death part of the cycle with a fixation on destruction
                        too fearful of losing control that you don’t express yourself
                        manipulative or psychically invasive";}
                    if($Date <1 || $Date >31){$flag = false;}
                break;
                case 11:
                    if($Date <= 22){$Image = "scorpio"; $Name = "SCORPIO"; $Time = "(24/10 – 22/11)"; $About = "SCORPIO IS THE SIGN OF SEXUALITY, THE SHADOWS, AND GREAT FEATS.
                        <br/>

                        You show power when you’re:
                        <br/>
                        exploring the rich, shadowy terrain of the psyche
                        administering strong medicine in a way that has integrity
                        engaged in life’s work that’s totally absorbing
                        aware of your power to heal and transform
                        patiently strategic when waiting for the right time
                        extending yourself to go into someone else’s darkness, for healing
                        soulful
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        heavy with unresolved emotions and dramas
                        stuck in the death part of the cycle with a fixation on destruction
                        too fearful of losing control that you don’t express yourself
                        manipulative or psychically invasive";}
                    if($Date >= 23){$Image = "sagittarius"; $Name = "SAGITTARIUS"; $Time = "(23/11 – 21/12)"; $About = "SAGITTARIUS IS THE SIGN OF KNOWLEDGE-SEEKING AND WANDERING FAR AFIELD.

                        <br/>
                        You show power when you’re:
                        <br/>
                        exploring new fields of study that fascinate you
                        planning things to look forward to
                        moving in and out of friend circles
                        sharing your optimistic outlook
                        joyful and friendly
                        testing your personal limits
                        experimenting at your creative edge
                        weaving in many ideas across disciplines
                        sharing your philosophy
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        bogged down in work that’s meaningless for you
                        alienating others by being intolerant";}
                    if($Date <1 || $Date >30){$flag = false;}
                break;
                case 12:
                    if($Date <= 21){$Image = "sagittarius"; $Name = "SAGITTARIUS"; $Time = "(23/11 – 21/12)"; $About = "SAGITTARIUS IS THE SIGN OF KNOWLEDGE-SEEKING AND WANDERING FAR AFIELD.

                        <br/>
                        You show power when you’re:
                        <br/>
                        exploring new fields of study that fascinate you
                        planning things to look forward to
                        moving in and out of friend circles
                        sharing your optimistic outlook
                        joyful and friendly
                        testing your personal limits
                        experimenting at your creative edge
                        weaving in many ideas across disciplines
                        sharing your philosophy
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        bogged down in work that’s meaningless for you
                        alienating others by being intolerant";}
                    if($Date >= 22){$Image = "capricorn"; $Name = "CAPRICORNUS"; $Time = "(22/12 – 20/1)"; $About = "CAPRICORN IS THE SIGN OF TRADITION, PERSEVERANCE AND LIFE’S WINTRY TIMES.

                        <br/>
                        You show power when you’re:
                        <br/>
                        committed to life’s work that’s deeply rewarding
                        exerting personal authority
                        feeling respected in your field or community
                        working toward mastery of skills
                        patience with your steady progress
                        compassionate toward your own melancholic feelings
                        <br/>
                        You feel powerless when you’re:
                        <br/>
                        all work and no play
                        unable to connect to wonder or mystery
                        too focused on status, convention
                        ruthless in attaining what you want
                        self-denigrating when you don’t meet your own high standards";}
                    if($Date <1 || $Date >31){$flag = false;}
                break;
                default:
                $flag = false;
            break;
            }           
        }
    ?>
<div>
    <form action="#" method="POST">
        <label for="signin">What is your zodiac ?</label>
        <div id="wrapper">
          <div id="arrow"></div>
          <input placeholder="Date" type="number" name="date" value="<?php echo $Date;?>"></input>
          <input placeholder="Month" type="number" name="month" value="<?php echo $Month;?>"></input>
        </div>
        <button type="submit" value="Searching">
          <span>
            Submit
          </span>
        </button>
      </form>
    </div>
      <?php
        if($flag == true){
            $result = ' <div class="about">
            <div class="col-left"><img src="./images/'.$Image.'.jpg" alt="'. $Name .'"/></div> 
            <div class="col-right">
            <div class="cont">
            <p>'. $Name . ''."  ".'' . $Time .'</p>
            <p id="pp">'. $About .'</p>
            </div>
            </div>
            </div>';
            echo $result;
        }else{
            $result = ' <div class="about"><h1>"Oops! Find not Found"</h1></div>';
            echo  $result;
        }    
        ?>
      <div id="hint">Click on the tabs</div>
</body>
</html>
```


>styles.css

```css
@import url(https://fonts.googleapis.com/css?family=Raleway:700,800);

html, body { margin: 0; }

:focus { outline: none; }
::-webkit-input-placeholder { color: #DEDFDF; }
::-moz-placeholder { color: #DEDFDF; }
:-moz-placeholder { color: #DEDFDF; }
::-ms-input-placeholder { color: #DEDFDF; }

body {
  background: #6ED0F6;
  color: #fff;
  font-family: 'Raleway', sans-serif;
  -webkit-font-smoothing: antialiased;
}

#wrapper, label, #arrow, button span { transition: all .5s cubic-bezier(.6,0,.4,1); }

#wrapper { overflow: hidden; }

#signin:checked ~ #wrapper { height: 178px; }
#signin:checked ~ #wrapper #arrow { left: 32px; }
#signin:checked ~ button span { transform: translate3d(0,-72px,0); }


form {
  width: 450px;
  height: 370px;
  margin: 15% 0px 0px 10%;
  float: left;
  position: absolute;
}

input[type=radio] { display: none; }

label {
  cursor: pointer;
  display: inline-block;
  font-size: 22px;
  font-weight: 800;
  color: #fff;
  margin-bottom: 30px;
  text-transform: uppercase;
}

label[for="signin"] { margin-right: 20px;}

input[type=number] {
  background: #fff;
  border: none;
  border-radius: 8px;
  font-size: 27px;
  font-family: 'Raleway', sans-serif;
  height: 72px;
  width: 99.5%;
  margin-bottom: 10px;
  opacity: 1;
  text-indent: 20px;
  transition: all .2s ease-in-out;
}
button {
  background: #079BCF;
  border: none;
  border-radius: 8px;
  color: #fff;
  cursor: pointer;
  font-family: 'Raleway', sans-serif;
  font-size: 27px;
  height: 72px;
  width: 100%;
  margin-bottom: 10px;
  overflow: hidden;
  transition: all .3s cubic-bezier(.6,0,.4,1);
}
button span {
  display: block;
  line-height: 72px;
  position: relative;
  top: -2px;
  transform: translate3d(0,0,0);
}
button:hover {
  background: #007BA5;
}

#arrow {
  height: 0;
  width: 0;
  border-bottom: 10px solid #fff;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  position: relative;
  left: 32px;
}


#hint {
  width: 100%;
  text-align: center;
  position: absolute;
  bottom: 20px;
}

.about {
    width: 50%;
    height: auto;
    margin: 10% 0px 0px 45%;
    border-radius: 5px ;
    position: absolute;
    background-color: #fff;
    display: flex;
  justify-content: center;
  align-items: center;
  }

img{
  margin: 10% 0 0 9%;
  width: 80%;
  height: auto;
}

.col-left{
  width: 50%;
  float: left;
}

.col-right{
  width: 50%;
  height: 100%;
  float: right;
  background-color: rgb(180, 186, 189);
}
.cont {
  width: 100%;
  margin: 30% 10% 10% 10%;
}

#pp{
  width: 80%;
  height: auto;
  line-height: 1.5;
}

h1{
  color: #007BA5;
  font-size: 35px;
  font-weight: 800;
  /* text-align: center;
  margin: 30%; */
}

```