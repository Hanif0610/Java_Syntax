# 연산자
### 연산자란 특정한 작업을 하기 위해서 사용되는 기호를 의미한다.
### 연산자는 실행에 따라서 대입, 산술, 비교, 논리 연산자 등이 있다.
## 산술 연산자
### 산술 연산자에는 더하기(+), 빼기(-), 곱하기(*), 나누기(/), 나머지(%) 이렇게 총 5가지 연산자가 존재한다.
System.out.println(1+2);
> 3

System.out.println(3-1);
> 2

System.out.println(4*5);
> 20

System.out.println(8/2);
> 4

System.out.println(9%3);
> 0
### 또한 연산자는 문자열과 문자열을 결합하는 과정에서도 사용이 된다.
public static void main(String[] ages)

{

    String a = "Java";
    String b = " Syntax";
    String c = a + b;
    System.out.println(c);
}
> Java Syntax
---
public static void main(String[] ages)

{

    int a = 3;
    int b = 10;
    float c = 10.0F;
    float d = 3.0F;
    System.out.println(b/a);
    System.out.println(c/a);
    Sysyem.out.println(c/d);
}
> 3

> 3.333333

> 3.333333
### 이렇게 정수와 정수, 실수와 정수, 실수와 실수도 연산자를 통해서 연산이 가능하다. 단 정수와 정수 연산의 결과에는 소수점이 붙지 않는다.
---
## 단항 연산자
### + / 양수(더하기)를 표현.
---
### - / 음수(빼기)를 표현.
---
### ++ / 증감 연산자. 값을 1증가시킨다.
---
### -- / 감소 연산자. 값을 1 감소시킨다.
### 증감 연산자와 감소 연산자는 붙는 위치에 따라서 연산 후 실행과 실행 후 연산으로 나뉘게 된다.
### 증감 연산자와 감소 연산자 둘 다 변수의 앞의 붙느냐, 뒤에 붙느냐에 따라서 연산이 다르게 진행된다.
public static void main(String[] ages)

{

    int a = 3;
    int b = 4;
    System.out.println(a++);
    System.out.println(++b);
    System.out.println(--a);
    System.out.println(b--);
}
> 3
### System.out.println(a++);에서 ++이 a의 뒤에 붙었으므로 화면에 a의 값인 3이 출력된 후 1증가가 되어 a의 값이 4가된다.
> 5
### 마찬가지로 System.out.println(++b);에서는 ++이 b앞에 붙어있으므로 b가 1증가하여 5가 된 후 화면에 출력된다.
> 3
### System.out.println(--a); 또한 전 코드에서 증가하여 4인 상태에서 전위감소이므로 1감소한 뒤에 화면에 출력되어 3이 출력된다.
> 5
### System.out.println(b--);에서도 동일하게 b가 5인 상태에서 후위감소이므로 화면에 5가 출력된 후에 1이 감소가 되어 b의 값은 다시 4가된다.
### a++ == a = a + 1/ a-- == a = a - 1