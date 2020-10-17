# Calc
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>JS Calculator</title>
    
    <link href="//db.onlinewebfonts.com/c/54ceb67fdeab6a229ffa41e9b663e5f8?family=LiquidCrystal" rel="stylesheet" type="text/css"/>

    <style type="text/css" media="all">
        *{
    margin: 0;
    padding:0;
    box-sizing: border-box;
    font-size: 20px;
    font-family: Helvetica;
}
p{
    font-size: 5px;
    font-weight: bold;
    font-family: fantasy;
    color: #CAD2C9;
    margin: 5px;
    text-align: right;
    padding-top: 5px;
    padding-right: 8px;
    color: #38764C;
}
body{
    background: #000000;
    margin: 10px;
}
.calc{
    width:242px;
    margin: 100px auto;
    height: 370px;
    border:5px solid #4F5752;
    border-radius:10px;
}
.display{
    border: 5px inset #918F8E;
    padding: 15px 0;
    padding-right: 5px;
    margin-top: 15px;
    margin:3px;
    margin-bottom: 5px;
    width: 225px;
    border-radius:5px;
    text-align: right;
    color:#9EA6A1;
    font-size:35px;
    font-family: "LiquidCrystal";
}

.keypad-table tr:first-child .key{
    background-color:#a5a5a5;
}
.keypad-table tr td:last-child .key{
    background-color: #F5863E;
}
.keypad-table tr:first-child .key:active{
background-color:#a5a5a590;
}
.keypad-table tr td:last-child .key:active{
background-color: #F5863E90;
}
.key{
    width:50px;
    height: 50px;
    border: 1px solid black;
    text-align: center;
    line-height:65px;
    border-radius:50px;
    margin-right: 7px;
    background:#333333;
    cursor:text ;
    user-select: none;
}
.key:active{
    background: #33333390;
}
    </style>
</head>
<body>

    <div class="calc">
        <div class="display">0</div>
        <div class="keypad">
            <table class="keypad-table">
                <tr>
                    <td>
                        <div class="key" onclick="allClear()">AC</div>
                    </td>
                    <td>
                        <div class="key" onclick="lastClear()">DEL</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay('%')">%</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay('/')">&divide;</div>
                    </td>
                </tr>
                <tr>
                    <td>
                        <div class="key" onclick="showDisplay(7)">7</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay(8)">8</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay(9)">9</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay('*')">&times;</div>
                    </td>
                </tr>
                <tr>
                    <td>
                        <div class="key" onclick="showDisplay(4)">4</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay(5)">5</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay(6)">6</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay('-')">&minus;</div>
                    </td>
                </tr>
                <tr>
                    <td>
                        <div class="key" onclick="showDisplay(1)">1</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay(2)">2</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay(3)">3</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay('+')">&plus;</div>
                    </td>
                </tr>
                <tr>
                    <td>
                        <div class="key" onclick="showDisplay(0)">0</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay('00')">00</div>
                    </td>
                    <td>
                        <div class="key" onclick="showDisplay('.')">.</div>
                    </td>
                    <td>
                        <div class="key" onclick="calculate()">&equals;</div>
                    </td>
                </tr>
            </table>
        </div>
        <p>Design by Kyaw, Copyright &copy;</p>
    </div>
    <script>
        
        var displayBox = document.querySelector(".display");
        
        var operator = ["+",'-','/','*','.','%'];
        
        function showDisplay(x){
            var current = displayBox.innerHTML;
            var lastIndex = current[current.length-1];
            
            if(displayBox.innerHTML == 0){
                return displayBox.innerHTML = x;
            }else if(operator.includes(x)&& operator.includes(lastIndex)){
                return displayBox.innerHTML = `${current.substring(0, current.length-1)}${x}`
                
            }
            return displayBox.innerHTML += x;
        }
        function calculate(){
            var current = displayBox.innerHTML;
            displayBox.innerHTML = eval(current)
        }
        function allClear(){
            displayBox.innerHTML = 0;
        }
        function lastClear(){
            var current = displayBox.innerHTML;
            if(current.length==1){
                displayBox.innerHTML = 0;
            }else{
            displayBox.innerHTML = current.substring(0, current.length-1);
            }
        }

    </script>

</body>
</html>
