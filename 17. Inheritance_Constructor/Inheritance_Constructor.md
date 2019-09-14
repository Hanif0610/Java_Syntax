{

    public class ConstructorDemo {
        public static void main(String[] args) {
            ConstructorDemo  c = new ConstructorDemo();
        }
    }
}
### 이 코드와 아래 코드는 비슷하지만 서로 다르다.
{

    public class ConstructorDemo {
        public ConstructorDemo(int param1) {}
        public static void main(String[] args) {
            ConstructorDemo  c = new ConstructorDemo();
        }
    }
}
### 1번째 코드에서는 main 자기 자신을 인스턴스화 시키는데, 생성자가 따로 존재하지 않아 객체를 생성할 때 자바에서 기본생성자를 만들기 때문에 오류가 발생하지 않는다.
### 허나 2번째 코드에서는 Class에 생성자를 선언했는데, 그 생성자에 매개변수가 존재하면 이 생성자가 기본 생성자가 아니라는 것을 의미함.
### 이 상태에서 Class를 인스턴스화 시키면 오류가 발생하게 된다.
### 1번 코드에서처럼 자바에서 기본생성자를 만드는데, 그 내용은 비어있기에 new ConstructorDemo();를 하게 되면 자바에서 만들어주기 때문에 오류가 발생하지 않는다.
### 2번 코드에서는 매개변수가 있는 생성자를 정의하고 있는데, 이 상태에서는 자바가 기본생성자를 만들지 않는다. 이 상태에서 new ConstructorDemo();를 해도 괄호 안에 인자가 없기 때문에 오류가 발생하게 된다.
{

    public class ConstructorDemo {
        public ConstructorDemo(){}
        public ConstructorDemo(int param1) {}
        public static void main(String[] args) {
            ConstructorDemo  c = new ConstructorDemo();
        }
    }
}
### class 바로 밑에 인자가 없는 생성자를 선언해주면 new ConstructorDemo();가 생성될 때 public ConstructorDemo(){}로 정의가 실행되기에 에러가 발생하지 않게 된다.
---
# super
{

    class Calculator {
        int left, right;
        
        public Calculator(int left, int right){
            this.left = left;
            this.right = right;
        }
        
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
        public SubstractionableCalculator(int left, int right) {
            this.left = left;
            this.right = right;
        }
    
        public void substract() {
            System.out.println(this.left - this.right);
        }
    }
    
    public class CalculatorConstructorDemo5 {
        public static void main(String[] args) {
            SubstractionableCalculator c1 = new SubstractionableCalculator(10, 20);
            c1.sum();
            c1.avg();
            c1.substract();
        }
    }
}
### 윗 코드를 실행시키면 오류는 다음과 같다.
Exception in thread "main" java.lang.Error: Unresolved compilation problem: 
    Implicit super constructor Calculator() is undefined. Must explicitly invoke another constructor
### 암시적으로 부모 Class에 Calculator라는 생성자가 정의돼있지 않다. 그래서 명시적으로 정의해야 한다. 라고 돼있다.
SubstractionableCalculator c1 = new SubstractionableCalculator(10, 20);
### 이 부분으로 인하여 이 명칭이 정의된 Class를 호출하는데, 호출하기 전 class SubstractionableCalculator의 부모 Class인 Calculator의 생성자를 자동으로 호출한다.
### 허나 Calculator에는 기본 생성자가 명시적 생성자가 존재하므로 자바에서 직업 기본 생성자를 만들지 않는다.
### 위 설명에서도 마찬가지로
public ConstructorDemo(){}


public Calculator(int left, int right)
### 이렇게 명시적 생성자 위에 public ConstructorDemo(){}붙임으로써 자바에서 기본 생성자를 만들게 할 수 있다.
### 하지만, 윗 코드를 고쳤다 가정할 때 Calculator(상위클래스)와, SubstractionableCalculator(하위클래스)에서 중복된 작업을 실행중이다.
### 둘 다 left, right를 받아 각각 this.left, this.right에 값을 넣는다.
### 상위 클래스와 하위 클래스 둘 다 생성자가 존재하고 서로 중복된 작업을 실행할 때, 하위 클래스에서 상위 클래스의 생성자의 코드를 복사하여 가져오고, 상위 클래스의 생성자를 하위 클래스가 생성될 때 생성자에서 호출하여 실행시킬 수 있게 된다.
> 바로 super라는 키워드를 사용하는 것이다.
{

    class Calculator {
        int left, right;
        
        public Calculator(){}
        
        public Calculator(int left, int right){
            this.left = left;
            this.right = right;
        }
        
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
        public SubstractionableCalculator(int left, int right) {
            super(left, right);
        }
    
        public void substract() {
            System.out.println(this.left - this.right);
        }
    }
    
    public class CalculatorConstructorDemo5 {
        public static void main(String[] args) {
            SubstractionableCalculator c1 = new SubstractionableCalculator(10, 20);
            c1.sum();
            c1.avg();
            c1.substract();
        }
    }
}
### 이전 코드와 달라진 점은 Class SubstractionableCalculator의 내용 뿐이다.
### super 키워드는 부모 클래스를 의미한다.
### 여기에 ()붙이면 부모 클래스의 생성자를 의미하게 된다.
### 이렇게 하면 부모 클래스의 기본 생성자가 없어져도 오류가 발생하지 않는다.
### 하위 클래스의 생성자에서 super를 사용할 때 주의할 점은 super가 가장 먼저 나타나야 한다는 점이다.
### 즉 부모가 초기화되기 전에 자식이 초기화되는 일을 방지하기 위한 정책이라고 생각하자.