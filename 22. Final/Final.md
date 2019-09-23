# Final
### 추상이 상속을 강제하는 것이라면 final은 상속/변경을 금지하는 규제다.
    class Calculator {
        static final double PI = 3.14;
        int left, right;
    
        public void setOprands(int left, int right) {
            this.left = left;
            this.right = right;
            //Calculator.PI = 6;
        }
    
        public void sum() {
            System.out.println(this.left + this.right);
        }
    
        public void avg() {
            System.out.println((this.left + this.right) / 2);
        }
    }
    
    public class CalculatorDemo1 {
        public static void main(String[] args) {
            Calculator c1 = new Calculator();
            System.out.println(c1.PI);
            //Calculator.PI = 10;
        }
    }
### 위 PI라는 변수에 final을 붙이면서 3.14라는 값이 더이상 변경할 수 없게 만든 것이다.
### main이나 setOprands에서 PI의 값을 변경하려는 코드들이 주석처리 돼있는데, 이 주석을 풀고 실행을 하면 final의 값을 변경할려고 하는 것이므로 에러가 발생하게 된다.
### final은 메소드와 클래스에서도 사용할 수 있으나, 사용빈도는 높지 않다.
    class A{
        final void b(){}
    }
    class B extends A{
        void b(){}
    }
### 위처럼 메소드에 final을 사용할 수 있다.
### 위 코드는 B라는 메소드에서 A라는 메소드를 상속하여 b라는 메소드를 오버라이딩하는 것이다.
### 허나 b라는 메소드는 final로 묶여있기 때문에 이 코드는 에러가 발생하게 된다.
    final class C{
        final void b(){}
    }
    class D extends C{}
### 또한 위 코드처럼 Class에도 final을 사용할 수 있다.
### 클래스에 final이 붙으면 더이상 상속할 수 없게 된다.
### 따라서 위 코드는 D라는 클래스가 C라는 코드를 상속할려고 하기에 위 코드 역시 에러가 발생하게 된다.