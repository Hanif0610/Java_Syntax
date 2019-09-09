# 상속
### 어떤 객체가 있을 때 그 객체의 필드(변수)와 메소드를 다른 객체가 물려 받을 수 있는 기능을 상속이라고 한다.
### 객체에 여러가지 메소드가 있을 때, 그 객체에다가 새로운 기능을 추가할 때 상속을 주로 사용한다.
### 객체에 메소드를 추가할 수 없는 경우
1. 허나 객체를 자신이 만든 것이 아닐때
2. 객체가 다양한 곳에서 활용되고 있는데 메소드를 추가하면 다른 곳에서는 불필요한 기능이 포함될 수 있을때
#### 1번 같은 경우 변경 할 수 있다고 해도 원 소스를 업데이트 하면 추가한 메소드가 사라지게 된다.
####  예를들어 새로운 메소드를 추가한 코드에서 원래 작업하던 코드를 붙여넣으면 코드가 사라지게 되므로 지속적으로 코드를 관리해야 한다.
#### 2번 같은 경우 자연스럽게 객체를 사용하는 입장에서 몰라도 되는 것까지 알아야 하는 문제가 된다.
### 정리하면  기존의 객체를 수정하지 않으면서 새로운 객체가 기존의 객체를 기반으로 만들어지게 되는 것이다.
### 이때 기존의 객체는 기능을 물려준다는 의미에서 부모 객체가 되고 새로운 객체는 기존 객체의 기능을 물려받는다는 의미에서 자식 객체가 된다.
> 부모 클래스와 자식 클래스의 관계를 상위(super) 클래스와 하위(sub) 클래스라고 표현하기도 한다. 또한 기초 클래스(base class), 유도 클래스(derived class)라고도 부른다.
### 예전 계산기 코드를 갖고 예를 들어보자
{

    class Calculator {
        int left, right;
    
        public void setOprands(int left, int right) {
            this.left = left;
            this.right = right;
        }
    
        public void sum() {
            System.out.println(this.left + this.right);
        }
    
        public void avg() {
            System.out.println((this.left + this.right) / 2);
        }
    }
    
    class SubstractionableCalculator extends Calculator {
        public void substract() {
            System.out.println(this.left - this.right);
        }
    }
    
    public class CalculatorDemo1 {
    
        public static void main(String[] args) {
    
            SubstractionableCalculator c1 = new SubstractionableCalculator();
            c1.setOprands(10, 20);
            c1.sum();
            c1.avg();
            c1.substract();
        }
    }
}
> 30

> 15

> -10
### 위 코드에서 SubstractionableCalculator이라는 클래스를 인스턴스화 시킨다.
### c1.setOprands, c1.sum, c1.avg은 이 전 계산기 코드에 존재했던 메소드이다.
### 그리고 c1.substract를 호출하면 SubstractionableCalculator라는 클래스 안으로 진입하게 된다.
### c1.setOprands, c1.sum, c1.avg은 이전 계산기 코드에 포함돼있던 코드지만, SubstractionableCalculator라는 것과 같이 사용할 수 있는 이유는 SubstractionableCalculator Class에 있는 extends Calculator 때문이다.
### 이것은 클래스 Calculator를 상속 받는다는 의미다.
### 즉, 상위 클래스인 Calculator를 하위 클래스인 SubstractionableCalculator가 확장하여 사용하기 때문이다.
### 그래서 따로 Calculator를 정의하지 않아도 호출이 가능한 것이다.
### 곱셈도 마찬가지이다.
{

    class MultiplicationableCalculator extends Calculator {
        public void multiplication() {
            System.out.println(this.left * this.right);
        }
    }
    
    public class CalculatorDemo2 {
        public static void main(String[] args) {
            MultiplicationableCalculator c1 = new MultiplicationableCalculator();
            c1.setOprands(10, 20);
            c1.sum();
            c1.avg();
            c1.multiplication();
        }
    }
}
### 이 전 코드와 마찬가지로 Calculator의 기능을 그대로 가져오면서 MultiplicationableCalculator라는 메소드를 추가로 정의하는 것이다.
### 또한 이미 한번 상속한 코드라도 또 상속이 가능하다.
{

    class DivisionableCalculator extends MultiplicationableCalculator {
        public void division() {
            System.out.println(this.left / this.right);
        }
    }
    
    public class CalculatorDemo3 {
        public static void main(String[] args) {
            DivisionableCalculator c1 = new DivisionableCalculator();
            c1.setOprands(10, 20);
            c1.sum();
            c1.avg();
            c1.multiplication();
            c1.division();
        }
    }
}