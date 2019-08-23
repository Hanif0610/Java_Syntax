# 조건문
### 조건문이란 주어진 조건에 따라서 실행을 다르게 동작하도록하는 것이다.
### 조건문의 종류에는 if~else문, switch~case문이 존재한다.
## if문
### if문은 if뒤에 있는 괄호에있는 조건을 따져 조건이 true면 중괄호 안에 있는 코드들을 실행한다. 단, 조건이 false면 실행을 하지 않는다.
if(true)

{

    System.out.println("True");
}
> True

if(false)

{

    System.out.println(Flase);
}
>아무것도 안뜸
### 이렇듯, if문의 조건을 판별하여 참이면 실행, 거짓이면 실행을 하지 않는다.
### 만약 맞으면 a, 아니면 b를 출력하고 싶을 때에는 else문을 사용한다.
## else문
public static void main(String[] args)

{

    int a = 1;
    int b = 3;
    if(a == b)
    {
        System.out.println("True");
    }
    else
    {
        System.out.println("False);
    }
}
> Flase

### if문의 조건을 확인하여 if문의 조건이 참이면 else를 실행하지 않고 넘어가지만, if문의 조건이 거짓이라면 if를 실행하지 않고 else문을 실행한다.
## else if문
### else if문은 if문과 else문을 합친 것으로 if문 다음에 다른 조건을 비교할 때 사용한다.
### if문의 값이 거짓이면 else if문으로 가서 조건을 확인한다. else if의 조건이 참이면 실행, 거짓이면 else로 넘어간다. else if는 여러개 나올 수 있으나 else의 뒤로는 갈 수 없다.
public static void main(String[] args)

{

    int a = 1;
    int b = 3;
    int c = 3;
    if(a == b)
    {
        System.out.println("True");
    }
    else if(b == c)
    {
        System.out.println("Same");
    }
    else
    {
        System.out.println("False);
    }
}
> Same
### 또한 조건문을 중첩하여 사용할 수도 있다.
public static void main(String[] args)

{

    int a = 1;
    int b = 1;
    int c == 3;
    int d == 4;
    if(a == b)
    {
        if(c == d)
        {
            System.out.println("true");
        }
        else
        {
            System.out.println("false");
        }
    }
    else
    {
        System.out.println("False);
    }
}
> true
---
## Switch case문
### 사람들은 대부분 if문을 사용하나, 조건이 많으면 switch case문을 사용하는 것도 괜찮다.
public static void main(String[] args)

{
         
    System.out.println("switch(2)");
    switch(2){
    case 1:
        System.out.println("one");
        break;
    case 2:
        System.out.println("two");
        break;
    case 3:
        System.out.println("three");
        break;
    default :
        System.out.println("four");
        break;
    }
}
> 2
### switch case문은 조건을 맨 처음부터 조건을 실행한다. case 1의 조건이 맞으면 출력 후 break;라는 것을 이용해서 조건문을 탈출한다. 만약 거짓이면 다음 case를 확인한다.
### 만약 case의 조건이 모두 거짓일경우 default문을 실행한다.