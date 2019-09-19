# 접근 제어자
### 접근 제어자는 사용자가 누가 이것을 사용할지에 대한 권한에 차등을 두는 것을 의미한다.
### 프로그래밍은 작은 것에서 거대한 것, 단순한 것에서 복잡한 것, 단독 작업에서 협업으로 나아가게 된다.
### 이러한 변화를 수용하기 위해서는 다양한 규제가 필요해지게 된다.
### 데이터 타입에서 int형 변수엔 정수만, char형 변수에는 문자만 들어가게끔 한 것도 규제라고 할 수 있다.
    class A {
        public String y(){
            return "public void y()";
        }
        private String z(){
            return "public void z()";
        }
        public String x(){
            return z();
        }
    }
    public class AccessDemo1 {
        public static void main(String[] args) {
            A a = new A();
            System.out.println(a.y());
            // 아래 코드는 오류가 발생한다.
            //System.out.println(a.z());
            System.out.println(a.x());
        }
    }
### Class A안에 존재하는 메소드들을 사용하기 위해서는 main에서 접근을 해야 한다.
### main에서 생성자로 Class를 인스턴스화 시킨 a라는 변수를 만들어 Class A에 접근을 하고 있다.
### 허나 Class A에 메소드에는 public이라는 것과 private라는 것이 존재한다.
### public은 누구나 접근이 가능하나, private는 Class A밖에서는 접근을 할 수 없다.
### 만약 System.out.println(a.z());의 주석을 풀고 실행시키면
>Exception in thread "main" java.lang.Error: Unresolved compilation problem:

>The method z() from the type A is not visible
### 라는 오류가 생긴다.
### 이는 메소드 z에 접근할 수 없다는 의미다.
### System.out.println(a.x()) 이 코드를 실행시키면 Class A에서는 return z();를 하고 있기 때문에 private인 z메소드에 접근이 가능하게 된다.
## 접근제어자의 사용 이유
### 규모있는 에플리케이션을 만드는 과정에서 경험하게 되는 수 많은 막장들로 인한 깊은 절망감을 경험해보지 않았다면 접근 제어자와 같은 개념들은 관념적인 것으로 치부되기 쉽다.
### 에플리케이션이 커진다는 것은 다른 말로 망가질 확률이 커진다는 의미와 같다.
### 특히 로직이 망가지는 첫번째 용의자는 사용자다.
### 즉 객체를 사용하는 입장에서 객체 내부적으로 사용하는 변수나 메소드에 접근함으로서 개발자가 의도하지 못한 오동작을 일으키게 되는 것이다.
### 이런 문제로부터 객체의 로직을 보호하기 위해서는 맴버에 따라서 외부의 접근을 허용하거나 차단해야 할 필요가 생긴다.
### 마치 은행이 누구나 접근 할 수 있는 창구와 관계자외에는 출입이 엄격하게 통제되는 금고를 구분하고 있는 이유와 같다.
### 접근 제어자를 사용하는 또 다른 이유는 사용자에게 객체를 조작 할 수 있는 수단만을 제공함으로서 결과적으로 객체의 사용에 집중 할 수 있도록 돕기 위함이다.
    class Calculator{
        private int left, right;
        
        public void setOprands(int left, int right){
            this.left = left;
            this.right = right;
        }
        private int _sum(){
            return this.left+this.right;
        }
        public void sumDecoPlus(){
            System.out.println("++++"+_sum()+"++++");
        }
        public void sumDecoMinus(){
            System.out.println("----"+_sum()+"----");
        }
    }
    
    public class CalculatorDemo {
        public static void main(String[] args) {        
            Calculator c1 = new Calculator();
            c1.setOprands(10, 20);
            c1.sumDecoPlus();
            c1.sumDecoMinus();
        }
    }
> ++++30++++

> ----30----
### 위 코드에서 left, right가 private로 돼있다.
### 이 두개의 변수는 객체 외부에서 호출될 필요가 없다. 따라서 외부로부터 이 변수를 숨기기 위해서 접근 제어자로 private을 지정했다.
### 또한 메소드 _sum이 추가 되었는데 실제 계산은 이 메소드가 내부적으로 처리하고, 계산된 결과를 외부에 출력해주는 메소드는 sumDecoPlus, sumDecoMinus에서 처리한다.
### 이상과 같은 조치를 통해서 사용자가 접근하면 안되거나 접근 할 필요가 없는 맴버에 대한 접근을 규제할 수 있게 되었다.
---
### 자바에서는 접근 제어자는 public, protected, default, private 이렇게 4가지로 존재한다.
### 각각의 접근 제어자들은 자료형 앞에 명시를 하는것이 원칙이나, 접근 제어자를 명시하지 않을 경우 자동적으로 default를 지정한다.
## public : 패키지, 클래스, 상속 관계 유무 상관없이 어느 곳에서나 사용이 가능하다.
## protected : public과 비슷하나 다른 패키지일때, 상속관계가 아닐 때는 사용이 불가능하다.(다른 패키지일때 상속 관계라면 사용 가능)
## default : 다른 패키지라면 사용이 불가능하다.
## private : 같은 패키지, 같은 클래스에서만 사용이 가능하다.
### 한가지 중요한 제약 사항이 있다. public 클래스가 포함된 소소코드는 public 클래스의 클래스 명과 소스코드의 파일명이 같아야 한다.
### 파일명이 ClassDemo.java라면 public Class 이름도 ClassDemo여야 한다.
### 또한  하나의 소스 코드에는 하나의 public 클래스가 존재 할 수 있다.