# 논리 연산자
### 논리 연사자(Conditional Operator)에는 &&(and), ||(or), !(not) 이렇게 3가지의 종류가 있다.
---
## And(&&)
### and연산자는 좌항과 우항이 모두 참일 때 참이된다.
public static void main(String[] args)

{

    if (true && true) {
        System.out.println(1);
    }

    if (true && false) {
        System.out.println(2);
    }

    if (false && true) {
        System.out.println(3);
    }

    if (false && false) {
        System.out.println(4);
    }
}
> 1
### 좌항과 우항이 둘 다 참일 때 참이므로 좌항과 우항이 둘 다 True인 1번째만 실행이 되는 것이다.
### 또한 논리 연산자는 중첩 조건문의 개수를 줄여줄수도 있다.
{

    int a = 1;
    int b = 2;
    if(a == 1)

    {

        if(b == 2)
        {
            System.out.println("True");
        }
        else
        {
            System.out.println("Flase");
        }
    }

    else

    {

        System.out.println("false");
    }
}
> True
### 이 코드에서 논리 연산자를 사용한다면
{

    int a = 1;
    int b = 2;
    if(a == 1 && b == 2)
    {
        System.out.println("True");
    }
    else
    {
        System.out.println("False");
    }
}
> True
### 이렇는 논리 연산자는 중첩 조건문의 조건문 개수를 줄여줄수도 있다.
## Or(||)
### or연산자는 좌항이나 우항 둘 중 하나만이라도 참이면 참이되는 연산자이다.
public static void main(String[] args)

{

    if (true || true) {
        System.out.println(1);
    }
    if (true || false) {
        System.out.println(2);
    }
    if (false || true) {
        System.out.println(3);
    }
    if (false || false) {
        System.out.println(4);
    }
}
> 1

> 2

> 3
### 이렇게 양 쪽 하나만이라도 참이라면 참이되는 것이 조건연산자이다.
## Not(!)
### not은 부정의 의미이기 때문에 참을 거짓으로, 거짓을 참으로 바꾸는 역할을 한다.
{

    if (!true) {
        System.out.println(1);
    }
    if (!false) {
        System.out.println(2);
    }
}
> 2
### 각각 True와 false에 각각 !가 붙었기 때문에 서로가 반전되어 !false값이 출력 된 것이다.