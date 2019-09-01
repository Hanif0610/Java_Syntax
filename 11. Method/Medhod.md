# 메소드
### 메소드(method)는 코드를 재사용할 수 있게 해준다.
public static void main(String[] args)

{

    return
}

여기서 void 부터 }까지, main부분을 메소드라고 한다.

{

    public static void numbering()
    {

        int i = 0;
        while (i < 10) {
            System.out.println(i);
            i++;
            }
        }

    public static void main(String[] args) {
        numbering();
    }
}
### main에서 numbering이라는 메소드를 호출하고 있다.
### 호출을 하면 정의된 곳으로 가서 그 안의 코드를 실행하게 된다.
### 만약 numbering();을 코드가 3줄이 있다면, 메소드가 정의된 곳의 코드를 3번 반복한다는 것을 의미한다.
### 메소드가 만약 없다면 윗줄에서 설명한 방법을 main에 직접 복사&붙여넣기로 수행할 만큼 호출 코드를 추가해야 할 것이다.
---
### main 메소드는 규칙이다.
### 코드를 짤 때는 반드시 public static void main(String[] args)가 이끄는 중괄호 안에 실행할 로직을 위치시켜야 한다.
###  main 메소드를 작성하고, 자바는 main 메소드를 실행하는 관계라고 할 수 있다.
---
## 인자
{

    public static void numbering(int limit) {
        int i = 0;
        while (i < limit) {
            System.out.println(i);
            i++;
        }
    }
 
    public static void main(String[] args) {
        numbering(5);
    }
}
### numbring이라는 함수에 5가 들어있고, void numbering에는 int limit이라는 변수가 들어가있다.
### 이렇듯 호출하는 함수 괄호에 숫자를 넣고, 정의된 함수의 괄호에 변수를 만들면, 그 변수에는 호출하는 괄호 안에 있는 숫자가 담기게 된다. //limit = 5;
### 이 값은 메소드 numbering의 중괄호 안에서만 사용할 수 있다.
### 여기서 전달되는 값을 '인자값'이라고 한다.
### numbering의 숫자를 바꾸게 된다면 limit안에 담기는 숫자도 바뀌게 되는 것이다.
### 또한 인자값은 복수로도 쓰일 수 있다.
{
 
    public static void numbering(int init, int limit) {
        int i = init;
        while (i < limit) {
            System.out.println(i);
            i++;
        }
    }
 
    public static void main(String[] args) {
        numbering(1, 5);
    }
}
### 이렇게 복수로 사용될 수 있다.
### 입력 값을 복수로 받고 싶다면 콤마 뒤에 매개변수를 정의해주면 된다. 또 이 메소스를 호출할 때는 매개변수의 순서대로 인자를 배치하면 된다.
---
## return
### 만약 main외의 메소드에서 연산이 진행된 후 그 값을 다시 main으로 가져오고 싶을 때는 return을 사용한다.