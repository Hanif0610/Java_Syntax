# Overloading
### 전 계산기 코드에서 3개의 값을 받을려면
> c1.setOprands(10, 20, 30);
### 로 값을 바꾼 후
    public void setOprands(int left, int right, int third){
    this.left = left;
    this.right = right;
    this.third = third;
    }
### 로 클래스 내부의 코드를 고치면 된다.
### 허나 여기서 2개의 값만 받는다 하면 third의 값은 전달이 안되어 에러가 발생한다.
### 그래서 main에서
c1.setOprands2(10, 20);

c1.setOprands3(10, 20, 30);
### 로 바꾸면 된다.
### 허나 매개변수의 수에 따라서 메소드의 이름이 달라지는 것은 왠지 깔끔한 방법이 아닌 것 같기에 다른 방법을 알아보도록 하겠다.
    class Calculator{
        int left, right;
        int third = 0;
        
        public void setOprands(int left, int right){
            System.out.println("setOprands(int left, int right)");
            this.left = left;
            this.right = right;
        }
        
        public void setOprands(int left, int right, int third){
            this.setOprands(left, right);
            System.out.println("setOprands(int left, int right, int third)");
            this.third = third;
        }
        
        public void sum(){
            System.out.println(this.left+this.right+this.third);
        }
        
        public void avg(){
            System.out.println((this.left+this.right+this.third)/3);
        }
    }
  
    public class CalculatorDemo {
      
        public static void main(String[] args) {
            
            Calculator c1 = new Calculator();
            c1.setOprands(10, 20);
            c1.sum();       
            c1.avg();
            c1.setOprands(10, 20, 30);
            c1.sum();       
            c1.avg();
            
        }
    }
### 위 코드처럼 main에서 각각 변수명은 같지만 매개변수가 다르게 2개를 설정한 후 Class에서 public void setOprands(int left, int right), public void setOprands(int left, int right, int third) 각각 이렇게 따로 설정을 해주었다.
### 같은 이름, 다른 매개변수의 형식 혹은 매개변수의 숫자에 의해서 오버로딩이 가능하다.
### 자바에선 메소드의 이름이 같다고 해도, 매개변수의 숫자나 매개변수의 데이터 타입이 다르면 다른 메소드로 인식을 한다.
### 이것을 오버로딩이라 한다.
### 즉, main에서 첫번째 setOprands는 매개변수가 2개이므로 매개변수가 2개인 메소드를 호출하고, 두번째 setOprands는 매개변수가 3개이므로 매개변수가 3개인 메소드를 호출하는 것이다.
### 만약 매개변수를 2개를 넣은 것을 호출했을 때 더하기와 평균 메소드에는 thrid가 추가되었기에 전역변수로 third는 0으로 지정을 한 것이다.
# Overloading의 규칙
### 메소드의 이름, 매개변수의 형식이나 숫자, 리턴타입이 같아야 오버로딩이 가능하다.
### 만약 같은 매개변수를 갖는 메소드가 리턴값이 다르면 오류가 발생한다.
    public class OverloadingDemo {
        void A (){System.out.println("void A()");}
        void A (int arg1){System.out.println("void A (int arg1)");}
        void A (String arg1){System.out.println("void A (String arg1)");}
        //int A (){System.out.println("void A()");}
        public static void main(String[] args) {
            OverloadingDemo od = new OverloadingDemo();
            od.A();
            od.A(1);
            od.A("coding everybody");
        }
    }
### 윗 코드는 문제는 없이 잘 실행이 되나, 만약 주석을 풀게 된다면 오류가 발생한다.
### 모두 리턴값이 void지만, 주석은 int를 반환하므로 오류가 발생하게 된다.
### 또한 오버로딩을 상속과 함께 사용이 가능하다.
    public class OverloadingDemo2 extends OverloadingDemo{
        void A (String arg1, String arg2){System.out.println("sub class : void A (String arg1, String arg2)");}
        void A (){System.out.println("sub class : void A ()");}
        public static void main(String[] args) {
            OverloadingDemo2 od = new OverloadingDemo2();
            od.A();
            od.A(1);
            od.A("coding everybody");
            od.A("coding everybody", "coding everybody");
            
        }
    }
### OverloadingDemo라는 클래스를 상속받고 있다.
### 이처럼 상속을 받은 후 코드를 추가하여 개선이 가능하다.
### 매개변수가 2개인 코드는 상위 클래스에서 A라는 변수가 존재하지만, 매개변수를 하나 더 추가한 것으로 overriding이 된다.
### 허나 인자가 없는 코드는 부모에서도 존재하기 때문에 이 역시 overriding이 된다.
## overriding VS overloading
### overriding : riding(올라탄다)을 이용해서 부모 클래스의 메소드의 동작방법을 변경
### overloading : loading을 이용해서 같은 이름, 다른 매개변수의 메소드들을 여러개 만들 수 있다는 사실을 아는 것
---
    class Calculator{
        int[] oprands;
        
        public void setOprands(int[] oprands){
            this.oprands = oprands;
        }
        
        public void sum(){
            int total = 0;
            for(int value : this.oprands){
                total += value;
            }
            System.out.println(total);
        }
        
        public void avg(){
            int total = 0;
            for(int value : this.oprands){
                total += value;
            }
            System.out.println(total/this.oprands.length);
        }
    }
    public class CalculatorDemo {
        public static void main(String[] args) {
            Calculator c1 = new Calculator();
            c1.setOprands(new int[]{10,20});
            c1.sum();       
            c1.avg();
            c1.setOprands(new int[]{10,20,30});
            c1.sum();       
            c1.avg();   
        }
    }
### 위의 코드는 인자로 배열을 사용하고 있다.
### 이렇게하면 하나의 인자로 여러개의 값을 받을 수 있다.