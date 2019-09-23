# Abstract
### Abstract란 한국어로 추상으로 번역된다.
### Abstract로 지정돼있는 메소드나 클래스는 직접적으로 사용할 수 없고 상속한 클래스를 만든 후 사용하도록 강제하는 것이다.
    abstract class A{
        public abstract int b();
        //본체가 있는 메소드는 abstract 키워드를 가질 수 없다.
        //public abstract int c(){System.out.println("Hello")}
        //추상 클래스 내에는 추상 메소드가 아닌 메소드가 존재 할 수 있다. 
        public void d(){
            System.out.println("world");
        }
    }
    public class AbstractDemo {
        public static void main(String[] args) {
            //A obj = new A();
        }
    }
### 만약 위 코드에서 main의 주석을 풀고 실행을 하게 된다면 에러가 발생하게 된다.
Exception in thread "main" java.lang.Error: Unresolved compilation problem:

Cannot instantiate the type A
### 클래스 A는 abstract라는 키워드로 정의돼있다.
### 이 키워드는 메소드 b는 메소드의 시그니처만 정의 되어 있고 이 메소드의 구체적인 구현은 하위 클래스에서 오버라이딩 해야 한다는 의미다.
### 이렇게 내용이 비어있는 메소드를 추상 메소드라고 부른다.
### 클래스의 맴버중 메소드 하나라도 abstract라면 클래스는 자동적으로 추상 클래스가 된다.
### 또한 추상 클래스에는 abstract가 붙지 않은 로직이 존재할 수 있다.
### 만약 저 위 코드에서 main위에 추상 클래스를 상속하여 오버라이딩 하는 코드가 존재한다면 이것은 에러를 발생시키지 않게 되는 것이다.
    abstract class A{
        public abstract int b();
        public void d(){
            System.out.println("world");
        }
    }

    public class B extends A {
        public int b(){
            return 1;
        }
    }
    public class AbstractDemo {
        public static void main(String[] args) {
            B obj = new B();
            System.out.println(obj.b());
        }
    }
### 추상 클래스를 B라는 클래스에서 상속을 받아서 추상 메소드의 리턴값인 int값을 반환을 해준 것이다.
### 이렇듯 추상 클래스는 상속을 받아서 오버라이딩을 하여 사용을 해야 한다.
### 추상 클래스는 상속을 강제하는 동시에 구체적인 로직을 담지 않고, 그 로직을 사용하기 위한 형식인 시그니처만을 담고 있다.
### 시그니처에 대한 구체적인 책임은 사용하는 쪽에 넘기는 것이 abstract이다.
## 사용하는 이유
### 추상 클래스는 소규모에서는 잘 쓰이지 않지만, 규모가 어느정도 있고 다양한 기능이 있을 때 기능의 공통적인 부분, 맥락에 따라 또는 사용 용도에 따라서 달라지는 기능들이 있을 때 그런 것들을 추상 클래스로 만든다.
### 즉, 상위 클래스(추상 클래스)에는 공통적으로 사용되는 로직이 들어가고, 상속받는 하위 클래스에는 용도에 따라 달라지는 로직을 구현한다.
    abstract class Calculator{
        int left, right;
        public void setOprands(int left, int right){
            this.left = left;
            this.right = right;
        } 
        public abstract void sum();  
        public abstract void avg();
        public void run(){
            sum();
            avg();
        }
    }
    class CalculatorDecoPlus extends Calculator {
        public void sum(){
            System.out.println("+ sum :"+(this.left+this.right));
        }
        public void avg(){
            System.out.println("+ avg :"+(this.left+this.right)/2);
        }
    } 
    class CalculatorDecoMinus extends Calculator {
        public void sum(){
            System.out.println("- sum :"+(this.left+this.right));
        }
        public void avg(){
            System.out.println("- avg :"+(this.left+this.right)/2);
        }
    } 
    public class CalculatorDemo {
        public static void main(String[] args) { 
            CalculatorDecoPlus c1 = new CalculatorDecoPlus();
            c1.setOprands(10, 20);
            c1.run();
            
            CalculatorDecoMinus c2 = new CalculatorDecoMinus();
            c2.setOprands(10, 20);
            c2.run();
        }
    }
> '+' sum : 30

> '+' avg : 15

> '-' sum : 30

> '-' avg : 15
### 위 코드는 합계(sum)를 실행하고 평균(avg)을 실행하는 절차를 메소드 run을 통해서 한 번에 실행되도록 한 코드이다.
### 만약 경우에 따라 합계와 평균을 화면에 출력하는 모습을 달리해야 하는 경우가 있을때, 상황에 따라 동작 방법을 달리하는 메소드를 추상 메소드로 만들어서 하위 클래스에서 구현하도록 하고 모든 클래스의 공통분모의 경우에는 상위 클래스에 두어서 코드의 중복, 유지보수의 편의성 등을 꾀할 수 있다.