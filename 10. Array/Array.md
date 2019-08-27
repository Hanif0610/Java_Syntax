# 배열
### 배열이란 자료형이 같은 변수들을 묶어논 것을 의미합니다.
### 배열은 여러 개의 데이터를 저장하기 위한 것이다.
String[] classGroup = { "최진혁", "최유빈", "한이람", "이고잉" };
### 배열은 데이터 타입 [] 변수명으로 생성이 가능하다.
### 여기서 []는 변수명 뒤에 사용될 수도 있다.
### 위 코드를 봤을 때 String[]은 데이터 타입이 String인 문자열 배열을 사용한다고 정의를 한 것이다.
### 여기서 classGroup은 배열이 아니라 문자열 데이터 타입을 갖는 변수가 된다.
### 또한 중괄호 안에 초기화를 할 때, 초기화 데이터들은 각각 쉼표로 구별한다.
### 배열의 각각 요소는 index라는 개념을 사용하는데, 이 인덱스로 각각의 데이터들을 가리킬 수 있게 된다.
public static void main(String[] args)

{

    int[] classGroup = { 1, 2, 3, 4 };
    System.out.println(classGroup[0]);
    System.out.println(classGroup[1]);
    System.out.println(classGroup[2]);
    System.out.println(classGroup[3]);
}
> 1

> 2

> 3

> 4
### 배열의 인덱스는 0으로 시작을 하게 된다. 맨 처음을 할때는 0번을, 맨 마지막 인덱스를 가리킬때는 '요소의 개수 - 1'의 숫자를 쓰면 된다.
### 또한 '변수명.length'으로 요소의 개수가 몇개인지를 알 수 있다.
public static void main(String[] args)

{
    int[] classGroup = new int[4];
    classGroup[0] = "11";
    System.out.println(classGroup.length);
    classGroup[1] = "12";
    System.out.println(classGroup.length);
    classGroup[2] = "13";
    System.out.println(classGroup.length);
    classGroup[3] = "14";
    System.out.println(classGroup.length);
}
> 4

> 4

> 4

> 4
### 이처럼 length는 배열이 무엇을 담고 있던 요소의 개수, 즉 배열의 길이를 출력하는 것을 알 수 있다.
### 배열은 반복문을 통하여 연속적인 작업을 수월히 사용할 수 있다.
 public static void main(String[] args)
 
 {
 
    String[] name = { "홍길동", "고길동", "김길동" };
    for (int i = 0; i < name.length; i++) {
        String member = name[i];
        System.out.println(member);
    }
}
> 홍길동

> 고길동

> 김길동
### 이처럼 배열의 요소를 하나씩 꺼내어 출력을 할 수 있다.
### 배열의 내용을 탐색할 때 for-each라는 것을 사용하는 방법이 있다.
public static void main(String[] args)

{

    String[] name = { "홍길동", "고길동", "김길동" };
    for (String e : name) {
        System.out.println(e);
    }
}
### 위 코드와 동일한 코드이나 문법적으로 좀 더 간결하게 바뀌었다.
## 오류 및 한계점
### 배열은 초기화할 때 그 크기가 정해져있다. 그래서 정해진 크기 이상의 값을 넣을 수 없다.
### 예를들어
String[] name = { "홍길동", "고길동", "김길동" };

System.out.println(name[3]);
### 인덱스는 0번부터 시작하고, 마지막 인덱스는 배열의 길이(요소의 개수) - 1이기에 name[3]은 이 배열에서 찾을 수 없기에 오류가 나게 된다.