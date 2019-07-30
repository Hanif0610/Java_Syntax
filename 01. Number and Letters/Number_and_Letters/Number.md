# 숫자와 문자
### 데이터 타입은 자료형 또는 데이터형이라고도 불린다.
---
## 숫자
---
### 따옴표가 없는 숫자는 숫자로 인식합니다. 따옴표가 있는 숫자는 문자로 해석을 한다.
System.out.println(1+2);\
System.out.println(4.3+6.5);\
System.out.println(3*7);\
System.out.println(10/2);

---
## 문자와 문자열
---
### 자바에서는 문자와 문자열을 각각 따로 구별한다.
### 문자는 '(작은따옴표)로 감싸며 문자열은 "(큰따옴표)로 감싸야 한다.
System.out.println('문');\
System.out.println("문자열");
### 만약 문자열을 작은따옴표로 감싸게 된다면 에러가 발생한다.
### 또한 문자 하나를 큰따옴표로 감싸면 문자열 처리가 될 수도 있기에 에러가 발생하지 않는다.
System.out.println("문");

### 문자끼리 또는 문자열 끼리도 연산이 가능하다.
System.out.println("문자의"+" 연산");
>문자의 연산

---
# 이스케이프
### 만약 문자열 안에 큰 따옴표를 넣을려면 \(백슬래쉬)를 이용한다.
System.out.println("egoing said \"Welcome programming world\"");
>egoing said "Welcom programming world"

### 만약 여러줄을 표기하고 싶을 때에는 \n을 사용한다.
System.out.println("HTML\nCSS\nJavaScript\n);
>HTML \
>CSS \
>JavaScript