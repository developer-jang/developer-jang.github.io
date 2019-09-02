---
title: String vs StringBuilder vs StringBuffer  
date: 2019-09-02 16:58:35  
tags:
- JAVA
- String
- StringBuilder
- StringBuffer
---
# String, StringBuilder, StringBuffer 차이

### 왜? :  
개발자 일을 시작하면서, 자바 기초책을 읽는다는 것은 자존심이 상할 때가 있었다.  

그러나 결국 자바의 기초가 중요하다고 생각하며  **자바의 신**을 읽게 되었다.

읽는 도중 String, StringBuilder, StringBuffer 차이의 언급을 보고 해당 Post를 작성하게 되었다.
  

### 공통점 :
단순히 보면 3가지 모두 문자열을 저장하고 관리하는 클래스

### 다른점 :

* String vs StringBuilder, StringBuffer
  * String : immutable 불변 객체
  * StringBuilder, StringBuffer : mutable 가변 객체
  
* StringBuilder vs StringBuffer
  * StringBuilder는 Synchronized가 걸려있지 않다.
  * StringBuffer는 Synchronized가 걸려있다.
  * 따라서, StringBuilder가 StringBuffer보다 속도측면에서는 빠르나, 안정성이 낮다.
  
* append 메소드 비교 (StringBuilder vs StringBuffer)

![StringBuffer] (/image/StringBuffer.png)  
![StringBuilder] (/image/StringBuilder.png)
  
### 설명 :

~~~ java
String url = "https://"
url += "naver.com"
~~~

위 예제만 본다면 문제가 될 것이 없다.

조금 세세히 들어가보면, stack 영역에 생성된 url 변수가 heap영역의 https://를 가리킨다. 

여기에 url += 를 하면 기존 https://에 값이 붙는 것이 아니라, 새로운 heap 영역에 더하기 연산을 수행한 결과가 할당 된다.

기존 heap 영역에 할당된 https://는 참조하지 않는 객체가 되고, 가비지 컬렉터의 대상이된다. 

### 결론 : 
* 개인적인 견해로는, 지역변수 형태로 사용을 할거면 StringBuilder를 사용하여 append하고, 클래스 변수나 인스턴스 변수로 사용한다면 StringBuffer를 사용한다.
* 속도 측면에서는 StringBuilder > StringBuffer > String
* 연산이 필요한 경우에는 StringBuilder나 StringBuffer를 사용하는 것을 권장한다.