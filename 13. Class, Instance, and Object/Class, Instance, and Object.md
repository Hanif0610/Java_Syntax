# 객체
### 객체란 변수와 메소드 등, 연관돼있는 기능별로 묶은 기능을 프로그래밍, 언어 차원에서 제공하는데 이 묶인 하나하나의 단위를 객체라고 한다.
ex) 게시판이 있을 때 게시판에 글을 쓰는 공간이 있다. 글을 쓰는데 필요한 메소드와 변수들이 각각 필요 할 것이다. 이러한 메소드와 변수들을 묶은 각각의 단위를 의미한다.
### 객체들은 각각 비슷한것끼리 모여 응집돼있다.
### 단 서로 연관돼있지 않은 객체들은 서로 껍질을 기준으로 분류된다.
### 이러한 객체들은 꼭 한곳에서만 쓰이는게 아닌, 다른 곳에서도 쓰일 수 있다.
---
# 클래스 & 인스턴스
### 클래스와 인스턴스는 서로 객체와 연관돼있다.
### 클래스는 객체를 만드는 설계도, 인스턴스는 설계도에 따라 만들어진 구체적인 제품을 의미한다.
### 클래스와 인스턴스를 사용하기 전에는 연산 과정은 같으나 숫자가 다를 경우, 일일히 코드를 직접 다 작성하였다.
public static void main(String[] args) {

    System.out.println(10 + 20);
    System.out.println(20 + 40);
}
> 30

> 60
### 윗 코드처럼 값은 다르지만 중복되는 연산과정을 일일히 작성하여 코드가 길어지게 되는데, 이런 중복된 코드를 제거하여 재활용성, 가독성, 유지보수성 등이 좋게 만드는 것을 메소드화 하는 것이다.
### 로직을 메소드로 만들면 코드의 양을 줄일 수 있고, 문제가 생겼을 때 원인을 더 쉽게 찾을 수 있다.
{

    public static void sum(int left, int right) {
        System.out.println(left + right);
    }
 
    public static void main(String[] args) {
        sum(10, 20);
        sum(20, 40);
    }
}
### 이전 코드와 실행 값은 동일하나 중복을 제거하였다.
### 기존의 코드와 동일히 작동하지만, 내용을 효율적으로 개선하는 것을 리펙토링(refactoring)이라 한다.
### 윗 코드에서 평균을 출력하겠다면 아래코드처럼 만들 수 있게된다.
{
 
    public static void avg(int left, int right) {
        System.out.println((left + right) / 2);
    }
 
    public static void sum(int left, int right) {
        System.out.println(left + right);
    }
 
    public static void main(String[] args) {
        int left, right;
 
        left = 10;
        right = 20;
 
        sum(left, right);
        avg(left, right);
 
        left = 20;
        right = 40;
 
        sum(left, right);
        avg(left, right);
    }
}
### left부터 avg, 다시 left부터 avg까지 각각 비슷한것 끼리 묶을 수 있게된다.
### 이렇게 연관돼있는 것들끼리 묶을 것인가를 고민하면서 만들어진 개념이 '객체지향'이다.
### 객체지향 프로그래밍은 로직을 상태(state)와 행위(behave)로 이루어진 객체로 만드는 것이다.
### 변수를 다른 말로는 상태(state)라고도 표현한다.
### 메소드를 다른 말로는 행동(behave)라고도 표현한다.
---
# 객체화
### 위 코드에서 메소드 sum과 avg는 변수 left와 right와 서로 연관 되어 있다.
### 또한 연관돼있는 것들이 반복을 한다.
class Calculator {

    int left, right;
    
    public void setOprands(int left, int right){
        this.left = left;
        this.right = right;
    }
    
    public void sum(){
        System.out.println(this.left+this.right);
    }
    
    public void avg(){
        System.out.println((this.left+this.right)/2);
    }
}

public class CalculatorDemo {
      
    public static void main(String[] args) {
          
        Calculator c1 = new Calculator();
        c1.setOprands(10, 20);
        c1.sum();       
        c1.avg();       
          
        Calculator c2 = new Calculator();
        c2.setOprands(20, 40);
        c2.sum();       
        c2.avg();
    }
  
}
### main에서 new Calculator는 새로운 객체를 만드는 것이다.
### 그리고 이 객체를 c1이라는 변수에 담는데, 이때 담는 변수의 자료형은 객체의 이름으로 지정한다.
### 이 코드의 시작부분에 class Calculator라는 것이 있는데, class는 Calculator라는 객체의 설계도를 알려주겠다 라는 것을 컴퓨터에게 알리는 역할을 한다.
### 여기서 Calculator는 main에서 만든 new Calculator()에 해당된다.
### new를 통해 새롭게 객체를 만들기 위해 필요한 설계도는 class Calculator안에 있는 코드들에 해당된다. 즉 new Calculator는 새로운 인스턴스를 생성하는 것이다.
### setOprands에서 들어가는 값은 메소드로 이동하여 각각 this.left, this.right에 들어가게 된다.
### 여기서 this는 c1에 담겨있는 Calculator라는 class를 구체적인 제품으로 만든 인스턴스를 가리키는 것이다.
### this.left라고 하면 class Calculator 내부에 생성한 int left를 가리키게 되는 것이다.
### 그렇기에 this.left = left를 통하여 setOprands에서 보낸 숫자를 담게 되는 것이다.
### 만약 this.left = this.left라고 하게 된다면 setOprands보낸 매게변수를 담는 것이 아닌, class Calculator에서 만든 left를 가리키게 된다. 따라서 우항에선 this.을 없애줘야 한다.
### 그리고 c1.sum()과 c1.avg()에서 각각 메소드로 이동하여 class Calculator 내부에 존재하는 값들로 연산 진행을 하게 된다.
---
## class 정리
> class Calculator {
### 위의 예에서 변수 left와 right, 메소드 sum과 avg는 연관되어 있는 로직이다. 이 로직들의 연관성은 계산을 하기 위한 것이다.
### 이 로직들을 대표하는 이름을 계산기라는 의미의 Calculator라고 정하고 이것들을 Calculator이라는 이름으로 그룹핑하고 싶다. 이럴 때 사용하는 키워드가 class이다.
### class 키워드 뒤에는 클래스 이름이 오고 그 뒤의 중괄호는 클래스의 시작과 끝의 경계를 의미한다.
### 즉, 클래스는 연관되어 있는 변수와 메소드의 집합이다.
## instance 정리
> Calculator c1 = new Calculator();
### new Calculator()은 클래스 Calculator를 구체적인 제품으로 만드는 명령이다. 이렇게 만들어진 구체적인 제품을 인스턴스(instance)라고 부른다.
---
> Calculator c1
### 위 코드처럼 c1의 자료형은 Calculator라는 클래스를 만들어서 사용한다.
### 클래스를 만든다는 것은 사용자 정의 데이터 타입을 만드는 것과 같은 의미다.
### 클래스를 인스턴스화 할 때는 변수에 담아야 한다는 것과 이 때 사용하는 변수의 데이터 타입은 그 클래스가 된다는 점이다.
### 일반적으로 설계도인 클래스가 구체적인 실체인 인스턴스가 되었을 때 객체라고 부른다.
### 보통은 구체적인 코드 상에서 나타는 객체를 인스턴스라고 부르고, 로직을 설계 할 때 나타나는 인스턴스를 객체라고 부른다.
### 또는 클래스, 인스턴스의 구분없이 포괄적으로 객체라는 말을 쓰기도 한다.
### 하나의 클래스여도 인스턴스가 다르면 다른 결과가 나타나게 된다.
### 하나의 클래스를 바탕으로 서로 다른 상태를 가진 인스턴스를 만들면 서로 다른 행동을 하게 된다는 것을 알 수 있다.
### 하나의 클래스가 여러개의 인스턴스가 될 수 있다는 점이 객체 지향이 제공하는 가장 기본적인 재활용성이라고 할 수 있다.