# 일단 만드는 Javascript

`실습으로 알아보는 Javascript`
[로또 번호 추첨기](#[로또-번호-추첨기])
[자소서 글자수 계산기](#[자소서-글자수-계산기])
[미니 스타크래프트](#[미니-스타크래프트])
[기념일 계산기](#[기념일-계산기])


<br/>
<br/>

### Javascript





### [로또 번호 추첨기]
---

JavaScript 사용 방법

1. html파일에서 js 작성
    
    <body></body> 태그가 끝나는 지점 바로 위쪽에 작성.
    
    <script></script> 태그로 감싸 JS 코드를 작성. 그래야 js코드임을 인식!
    
    document.write(”안녕”)
    
    따옴표 안에있는 문장을 화면에 출력하는 코드
    
2. JS파일로 작성
    
    `myScript.js` 파일을 만든 후 파일에 js 코드를 작성.
    
    사용하고싶은 html의 코드에 `<script src='myScript.js'></script>` 코드 추가

---
js는 유연한 언어이므로 코드의 끝에 ;를 붙이는 것이 아닌, 줄바꿈으로도 코드의 끝을 나타낼 수 있다. 하지만 여러줄의 코드를 줄바꿈없이 작성한다면, 해당 코드를 인식하지 못한다. 이러한 경우 코드의 끝을 나타내기위해 ;를 붙여줄 시 여러줄의 코드를 한줄로 작성하더라도 제대로 인식한다.

주석의 용도

1. 코드 설명을 적어줄 때
2. 코드를 동작시키고 싶지 않을 때

`//` 를 사용해 주석처리한다.

여러줄의 주석을 사용 시 `/**/` 을 사용해 나타낸다.

---

변수를 선언할 땐 var 키워드를 사용한다.

js는 파이썬과 비슷하게 자료형 선언없이 변수를 선언할 수 있다.

자료형이 무엇인지 알고싶을때는 `typeof 변수`를 사용하여 해당 변수의 자료형으로 값이 반환되므로 자료형을 알아낼 수 있다.

---

```jsx
Math.random();  // 0이상 ~ 1미만 실수 (float) 출력
Math.random() * 45;  // 0이상 ~ 45미만 실수(float) 출력
Math.random() * 45 + 1;  // 1이상 ~ 46미만 실수(float) 출력
parseInt(num);  // 실수형인 num을 정수형으로 변환, 소수점을 버림
parseInt(Math.random() * 45 + 1);  // 1이상 ~ 45이하 정수(int) 출력
```

```jsx
<body>
    <h1>로또 번호 추첨기 1</h1>
    <script>
        var num = Math.random() * 45 + 1;
        var ball1 = parseInt(num);
        document.write(ball1);
    </script>
</body> 
```

---

배열을 만들 수 있으며 인덱스는 0부터 시작한다.

```jsx
<script>
	var lotto = [1,2,3,4,5,6];
	lotto.push(7);  // .push() 함수를 사용해 배열에 마지막 값 7 추가
	document.write(lotto);
</script> 
```

---

`**DRY**`  Don’t Repeat Yourself

반복되는 코드를 작성하고있다면, 어떻게하여 반복적이지 않게 코드를 작성할지 고민해라

반복문 - for, while 을 사용

```jsx
<script>
	var lotto = [];
	for (var i = 0; i < 6; i++){
		lotto.push(parseInt(Math.random() * 45 + 1));
	}
	document.write(lotto);
</script>
```

---

로또번호는 중복이 있으면 안됨. 이를 조건문을 사용해 해결해보자

```jsx
배열.indexOF(값) // 값이 있으면 위치, 없으면 -1을 반환

<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        for (var i = 0; i < 6; i++){
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) {
                lotto.push(num);
            }
        }
        document.write(lotto);
    </script>
</body>
```
---

```jsx
배열.length // 배열의 길이를 반환

<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        while (lotto.length < 6) {
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) {
                lotto.push(num);
            }
        }
        document.write(lotto);
    </script>
</body>
```

---

```jsx
배열.sort() // 배열 값 정렬

var lotto = [1,2,3,33,22,11];
lotto.sort(); // 사전순으로 정렬, 즉 앞자리를 기준으로 정렬됨.
document.write(lotto);

lotto.sort((a,b)=>a-b); // 숫자의 크기순으로 정렬하고자 익명함수를 사용해 정렬
lotto.sort((a,b)=>b-a); // 내림차순 정렬
```

```jsx
// 완성 코드
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기</title>
</head>
<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        while (lotto.length < 6) {
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) {
                lotto.push(num);
            }
        }
        lotto.sort((a,b)=>a-b);
        document.write(lotto);
    </script>
</body>
</html>
```

```jsx
// 완성 코드에 html/css를 곁들인 ...
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        while (lotto.length < 6) {
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) {
                lotto.push(num);
            }
        }
        lotto.sort((a,b)=>a-b);
        document.write("<div class='ball ball1'>" + lotto[0] + "</div>");
        document.write("<div class='ball ball2'>" + lotto[1] + "</div>");
        document.write("<div class='ball ball3'>" + lotto[2] + "</div>");
        document.write("<div class='ball ball4'>" + lotto[3] + "</div>");
        document.write("<div class='ball ball5'>" + lotto[4] + "</div>");
        document.write("<div class='ball ball6'>" + lotto[5] + "</div>");
    </script>
</body>
</html>
```

<br/>
<br/>

### [자소서 글자수 계산기]
---
글 작성 시 글자수가 바뀌며 현재 글자수가 몇글자인지 알려주는 코드 작성.

또한 최대글자수가 넘어가면 작성이 안되도록 코딩.

---

**Document Object Model**

웹화면을 구성하는 html 코드를 쉽게 접근할 수 있도록 만든 모델

JS는 DOM을 활용해 화면을 구성하는 모든것들에 접근할 수 있으며 원하는대로 바꿀 수 있다.

---

JS로 DOM에 접근하여 원하는 값을 가져와보자

자바스크립트에서 document는 DOM의 진입점 역할로, 화면의 html을 불러와 `document.getElementById(’id’);` 를 통해 특정 id를 가진 태그를 가져올 수 있다.

```jsx
document.getElementById(’id’).value; // 태그로 감싸진 값을 가져옴
document.getElementById(’id’).innerHTML; // 태그로 감싸진 값을 가져옴
```

새로운 출력방법을 알아보자!

이전 출력방법 → `document.write()`

`console.log('hi');`

```jsx
var content = document.getElementById('jasoseol').value;
console.log(content);
```

---

가져온 값의 글자수를 세보자!

```jsx
var content = document.getElementById('jasoseol').value;
console.log(content.length); // 문자열의 길이를 반환해 출력
```

---

계산한 글자수를 웹에 출력해보자. 특정 값을 원하는 형태로 웹화면에 출력해보자.

```jsx
<body class="container">
    <textarea class="form-control" rows="3" id="jasoseol">글자수세기</textarea>
    <span id="count">(0/200)</span>
    <script>
        var content = document.getElementById('jasoseol').value;
        document.getElementById('count').innerHTML = '(' + content.length + '/200)';
    </script>
</body>
```

`document.getElementById('count').innerHTML = '(' + content.length + '/200)';`

html의 count 태그로 감싸진 html을 `'(' + content.length + '/200)'`로 할당.

---

함수를 사용해 긴 코드를 여러번 쓰지않고 만들자.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1d622cfa-1a9d-4dbc-a595-0085fc8a8c9e/Untitled.png)

```jsx
<script>
	function counter() {
		var content = document.getElementById('jasoseol').value;
		document.getElementById('count').innerHTML = '(' + content.length + '/200)';
	};
	counter();
</script>
```

---

글자를 쓸 때마다 자동으로 글자수를 세보자!

→ 키보드를 누를 때마다 글자수를 세자. 

이벤트란, 마우스 클릭, 키보드 누름, 값 변화, 페이지 로딩 등 어떤 사건을 의미.

이벤트 핸들링이란, ‘이벤트가 발생하면 ~~ 해라’라는 코드를 의미

<textarea 이벤트=이벤트핸들링></textarea>

```jsx
<body class="container"> 
    <textarea onkeydown='counter();' id="jasoseol">글자수세기</textarea>
    <span id="count">(0/200)</span>
    <script>
        function counter() {
            var content = document.getElementById('jasoseol').value;
            document.getElementById('count').innerHTML = '(' + content.length + '/200)';
        }
        counter();
    </script>
</body>
```

`<textarea onkeydown='counter();' id="jasoseol">글자수세기</textarea>`

해당 코드 위치의 html에서 이벤트가 발생시 이벤트핸들링으로 counter()함수가 실행

---

특정 글자수를 넘기면 더이상 작성을 하지 못하도록 해보자.

문자열.substring(0,10); // 문자열을 자르는 함수

```jsx
문자열.substring(0,10); // 문자열을 자르는 함수

<script>
        function counter() {
            var content = document.getElementById('jasoseol').value;
            if (content.length > 200) {
                content = content.substring(0,200);
								document.getElementById('jasoseol').value = content;
            }
            document.getElementById('count').innerHTML = '(' + content.length + '/200)';
        }
        counter();
    </script>
```

---

```jsx
<body class='container'>
    <h1>글자수세기</h1>
    <textarea class="form-control" rows="3" id="jasoseol" onkeydown="counter();">글작성 ... </textarea>
    <span id="count">(0/200)</span>
    <script>
        function counter() {
            var content = document.getElementById('jasoseol').value;
            if (content.length > 200) {
                content = content.substring(0,200);
                document.getElementById('jasoseol').value = content;
            }
            document.getElementById('count').innerHTML = '(' + content.length + '/200)';
        }
        counter();
    </script>
</body>
```


<br/>
<br/>

### [미니 스타크래프트]
---

js는 돔을 제어하여 html 요소를 선택하여 값을 가져올 수 있다.

jQuery 라이브러리를 사용하면 짧은 코드로 돔을 활용해 html에서 원하는 값을 가져올 수 있다.

**jQuery 장점**

1. 간결한 문법
2. 편리한 API
3. 크로스 브라우징
    
    모든 브라우저 모든 버전에서 동일한 동작을 할 수 있다.
    

**사용방법**

[code.jquery.com](http://code.jquery.com) 페이지에 접속하여 minified를 클릭해 코드를 복사해 사용하고자하는 html에 붙여넣는다.

**기본 문법**

$(선택자).행위;

선택자는 css 문법과 동일하게 사용된다.

```jsx
<body>
    <h1>jQuery 기초</h1>
    <textarea id="content">jQuery를 배워보자</textarea>
    <script
    src="https://code.jquery.com/jquery-3.5.1.js"
    integrity="sha256-QWo7LDvxbWT2tbbQ97B53yJnYU3WhH/C8ycbRAkjPDc="
    crossorigin="anonymous"></script>
    <script>
        console.log($('#content').val());
    </script>
</body>
```

---

jQuery를 사용해 이벤트를 사용해보자!

```jsx
<button id="click" onclick="hello();">클릭</button>
$('#click').click(hello);
```
.click을 했을 때 hello라는 함수가 실행

아래 두 개의 코드는 동일한 실행결과를 갖는다.

```jsx
<body>
    <h1>jQuery 이벤트</h1>
    <button id="click" onclick="hello();">클릭</button>
    <script
  src="https://code.jquery.com/jquery-3.5.1.min.js"
  integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
  crossorigin="anonymous"></script>
    <script>
        function hello() {
            console.log('hello');
        }
    </script>
</body>
```

```jsx
<body>
    <h1>jQuery 이벤트</h1>
    <button id="click">클릭</button>
    <script
  src="https://code.jquery.com/jquery-3.5.1.min.js"
  integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
  crossorigin="anonymous"></script>
    <script>
        function hello() {
            console.log('hello');
        }
        $('#click').click(hello);
    </script>
</body>
```

---

익명함수란? 이름이 없는 함수

함수는 **정의**부분에 해당 함수의 코드를 작성한 후 **호출**을 통해 함수를 실행한다.

하지만 단 한번만 실행한다면, 위의 과정은 너무 비효율적이다.

이를 위해 익명함수를 사용하여 함수의 정의없이 바로 사용할 수 있도록 한다.

```jsx
<body>
    <h1>익명 함수</h1>
    <button id="click">클릭</button>
    <script
  src="https://code.jquery.com/jquery-3.5.1.min.js"
  integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
  crossorigin="anonymous"></script>
    <script>
        $('#click').click(function(){
            console.log('hello');
        });
    </script>
</body>
```

---


<br/>
<br/>

### [기념일 계산기]