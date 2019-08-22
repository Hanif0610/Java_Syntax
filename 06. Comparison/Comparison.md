# 비교
## Boolean
### Boolean(불린)은 참(True)과 거짓(False) 이렇게 2가지를 갖는 데이터 타입이다.
---
## 비교(관계) 연산자
### 비교 연산자는 주어진 값들의 값이 서로 같은지, 다른지, 큰지, 작은지를 구분하는 역할을 한다.
### 조건을 통하여 값이 일치하면 True, 불일치하면 False를 반환한다.
### 둘의 결과가 같은지를 비교하는 연산자는 '=='이다.
### '='을 한개만 쓴다면 대입이지만, 두개를 쓴다면 두 항이 서로 같은지를 비교하게 된다.
System.out.println(31==32);
> false

System.out.println(25==25);
> true

System.out.println("first"=="second");
> false

System.out.println("first"=="first");
>true
---
### '!='연산자는 두 항이 다른지를 비교하는 연산자이다.
### 따라서 비교하였을 때 서로 다르면 true, 같으면 false를 반환한다.
System.out.println(42!=40);
> true

System.out.println(20!=20);
> false

System.out.println("big"!="small");
> true

System.out.println("big"!="big");
> false
---
### '>'은 좌항이 우항보다 큰지를 비교하는 연산이다. '<'는 반대의 의미가 된다.
System.out.println(50>60);
> false

System.out.println(27<35);
>true

System.out.println(10>10);
>false
---
### '>='은 좌항이 우항보다 크거나 같은지를 비교하는 연산이다. 마찬가지로 '<='는 반대의 의미이다.
System.out.println(70 <= 15);
> false

System.out.println(60 >= 20);
> true

System.out.println(17 >= 17);
>true
---
### '.equals'는 문자열을 비교할 때 사용되는 메소드이다.
### '.equals'는 외향을 비교하는 것이 아닌 내부를 비교하는 메소드이다.
public static void main(String[] ages)

{

    String a = "Hello world";
    String b = new String("Hello world");
    System.out.println(a == b);
    System.out.println(a.equals(b));
}
> false

>true
### new String이라는 것을 사용하면 새로운 문자열을 생성할 수 있다.
### 따라서 a == b로 비교를 하면 일반 String과 new String으로 비교가 되어서 false를 반환하지만, .equals를 사용하면 내부에 들어있는 Hello world를 비교하기에 true를 반환한다.