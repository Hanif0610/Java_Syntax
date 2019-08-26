# for
### for문 형식은 아래와 같다.
for(초기값; 조건식(종료조건); 증가값(반복실행))

{

    실행 구문
}
### 이렇게 for문은 괄호 안에는 초기값, 조건식, 증가값이 한번에 다 들어간다.
### 여기서 중요한 것은 for문에서 각각의 값을 나눠주는 역할을 세미콜론(;)이 한다는 것이다.
### 초기화 : 반복문이 실행될 때 1회 실행된다.
### 종료조건 : 초기화가 실행된 후에 종료조건이 실행된다. 종료조건의 값이 false일 때까지 반복문의 중괄호 구간의 코드가 반복 실행된다.
### 중괄호 구간의 실행이 끝나면 반복 실행이 실행된다. 일반적으로 이 곳에 i++와 같이 변수를 증가시키는 로직이 위치하고, 이것이 실행된 후에 종료조건이 실행된다. 종료조건이 false가 될 때까지 이 과정이 반복된다.
### 또한 for문은 초기값과 while문을 합쳐둔 것이라 볼 수 있다.
public static void main(String[] args)

{

    int i = 0;
    while(i < 10)
    {
        System.out.println(i);
        i++;
    }
}
### 이 코드를 for문으로 바꾸게 되면
public static void main(String[] args)

{

    int i;
    for(i = 0; i < 10; i++)
    {
        System.out.println(i);
    }
}
### 또한 for문은 여러번 중첩하여 사용이 가능하다.
public static void main(String[] args)

{

    for(int i = 2; i < 10; i++)
    {
        for(int j = 1; j < 10; j++)
        {
            System.out.println(j + "+" + i + "=" + j*i);
        }
        System.out.println("\n");
    }
}
### 위 코드는 이중 for문으로 구구단을 출력하는 코드이다.
### 이처럼 for문을 중첩으로 사용하여 여러가지 상황에 응용이 가능하다.
### 또한 for문도 while문 처럼 break와 continue로 반복문 제어가 가능하다.
public static void main(String[] args)
{

    for (int i = 0; i < 10; i++) {
        if (i == 5) break;
        System.out.println(i);
    }
}
> 1

> 2

> 3

> 4

 public static void main(String[] args)
 
 {

    for (int i = 0; i < 10; i++) {
        if (i == 5) continue;
        System.out.println(i);
    }
}
> 1

> 2

> 3

> 4

> 6

> 7

> 8

> 9