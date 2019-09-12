# 초기화
### 초기화는 어떤 일을 시작하기 전에 준비를 하는 것이다.
### 함수를 호출할 때 값을 지정하지 않고 호출을 하게 된다면, 원하는 결과를 얻을 수 없게된다.
{

    Calculator c1 = new Calculator();
    c1.sum();       
    c1.avg();
}
### 위 코드처럼 인스턴스를 생성 후 값을 지정하지 않았기에 코드에서 오류가 발생한다.
### 그래서 반드시 생성한 후 값을 지정해줘야 한다.
### 이렇게 함수를 호출하기 전, 값을 지정해주는 작업이 초기화에 해당된다.
# 생성자
### 위 오류를 해결하는 방법에는 생성자를 이용하는 방법이 있다.
{

    Calculator c1 = new Calculator(10, 20);
    c1.sum();
    c1.avg();
}
### 이렇듯, 생성할 때 부터 값을 지정하면 오류를 해결할 수 있게 된다.
{

    class Calculator {
        int left, right;
    
        public Calculator(int left, int right) {
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
    
    public class CalculatorDemo1 {
    
        public static void main(String[] args) {
    
            Calculator c1 = new Calculator(10, 20);
            c1.sum();
            c1.avg();
    
            Calculator c2 = new Calculator(20, 40);
            c2.sum();
            c2.avg();
        }    
    }
}
### 위 코드에서 Class의 이름과 public의 이름이 동일한 것을 볼 수 있다.
### 이때 public Calculator 이것을 생성자라고 한다.
### 여기서 Calculator c1 = new Calculator(10, 20);에서의 new Calculator를 Class에 대한 생성자라고 한다.
### 생성자 덕분에 Calculator 객체를 사용하기 위해서 사실상 반드시 필요한 작업이라고 할 수 있는 좌항(left)과 우항(right)의 값을 설정하는 과정을 객체 생성 과정에서 강제할 수 있게 되었다.
### 생성자는 Class가 실행될 때 자동으로 Class와 똑같은 이름을 갖는 생성자가 생성되도록 약속돼있다.
### 이 생성자가 다른 메소드보다 먼저 실행이 되도록 약속돼있다.
### 즉, Class와 이름이 똑같은 생성자를 설정해둔다면, 어떠한 메소드보다 제일 먼저 실행이 되게 된다.
## 생성자의 특징
- 값을 반환하지 않는다.
    - 생성자는 인스턴스를 생성해주는 역할을 하는 특수한 메소드라고 할 수 있다. 그런데 반환 값이 있다면 엉뚱한 객체가 생성될 것이다. 따라서 반환 값을 필요로하는 작업에서는 생성자를 사용하지 않는다. 반환 값이 없기 때문에 return도 사용하지 않고, 반환 값을 메소드 정의에 포함시키지도 않는다.
- 생성자의 이름은 클래스의 이름과 동일하다.
    - 자바에서 클래스의 이름과 동일한 메소드는 생성자로 사용하기로 약속되어 있다.