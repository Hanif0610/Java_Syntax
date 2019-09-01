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
<<<<<<< HEAD
=======
}
>>>>>>> d5f10e3e9e069cf65d33292d5fe44e9e1848d48f
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
<<<<<<< HEAD
=======
}
>>>>>>> d5f10e3e9e069cf65d33292d5fe44e9e1848d48f
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
<<<<<<< HEAD
=======
}
>>>>>>> d5f10e3e9e069cf65d33292d5fe44e9e1848d48f
### 이렇게 복수로 사용될 수 있다.
### 입력 값을 복수로 받고 싶다면 콤마 뒤에 매개변수를 정의해주면 된다. 또 이 메소스를 호출할 때는 매개변수의 순서대로 인자를 배치하면 된다.
---
## return
<<<<<<< HEAD
### 만약 main외의 메소드에서 연산이 진행된 후 그 값을 다시 main으로 가져오고 싶을 때는 return을 사용한다.

{

    public static String numbering(int init, int limit) {
        int i = init;
        String output = "";
        while (i < limit) {
            output += i;
            i++;
        }
        return output;
    }
 
    public static void main(String[] args) {
        String result = numbering(1, 5);
        System.out.println(result);
    }
### 윗 코드는 numbering 메소드에서 1부터 4까지의 합을 구한 뒤 구한 값을 매인으로 가져와 출력하는 코드이다.
### 이처럼, main 밖에서 연산을 진행 후 결과를 main으로 가져올 수도 있다.
### return을 할 때 리턴값이 있으면 그 자료형에 맞는 것을 쓰면 되나, 리턴값이 없을 경우 void를 주로 사용한다.
### 또한 조건문을 활용하여 return값을 활용할 수도 있다.
{

    public static String num(int i) {
        if(i==0){
            return "zero";
        } else if(i==1){
            return "one";
        } else if(i==2){
            return "two";
        }
        return "none";
    }
 
    public static void main(String[] args) {
        System.out.println(num(1));
    }
### 또한 배열을 return할 수도 있다.
{
 
    public static String[] getMembers() {
        String[] members = { "최진혁", "최유빈", "한이람" };
        return members;
    }
 
    public static void main(String[] args) {
        String[] members = getMembers();
    }
=======
### 만약 main외의 메소드에서 연산이 진행된 후 그 값을 다시 main으로 가져오고 싶을 때는 return을 사용한다.
>>>>>>> d5f10e3e9e069cf65d33292d5fe44e9e1848d48f
