# Overriding
### 오버라이딩은 상속은 하되 필요에 맞게 재정의하여 기능을 변경하는 것이다.
### 이 전에 올린 코드를 한곳만 수정할 것이다.
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
        
        public void sum() {
            System.out.println("실행 결과는 " +(this.left + this.right)+"입니다.");
        }
        
        public void substract() {
            System.out.println(this.left - this.right);
        }
    }
    
    public class CalculatorDemo {
        public static void main(String[] args) {
            SubstractionableCalculator c1 = new SubstractionableCalculator();
            c1.setOprands(10, 20);
            c1.sum();
            c1.avg();
            c1.substract();
        }
    }
>실행 결과는 30입니다.


>15


>-10
### Calculator라는 class에 sum함수가 정의돼있지만, 하위 클래스에서도 sum이 정의가 돼있다.
### 이는 상위 클래스에 있는 내용을 하위 클래스에 재정의 한 것이다.
### c1이란 변수는 하위 클래스를 인스턴스화 시킨 것이기에 호출을 할 때 하위 클래스에 정의된 함수가 호출이 된 것이다.
# Overriding의 조건
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
        
        public void sum() {
            System.out.println("실행 결과는 " +(this.left + this.right)+"입니다.");
        }
        
        public int avg() {
            return (this.left + this.right)/2;
        }
        
        public void substract() {
            System.out.println(this.left - this.right);
        }
    }
    
    public class CalculatorDemo {
        public static void main(String[] args) {
            SubstractionableCalculator c1 = new SubstractionableCalculator();
            c1.setOprands(10, 20);
            c1.sum();
            c1.avg();
            c1.substract();
        }
    }
### 이 전 코드에서 하위 클래스에 avg를 return하는 코드를 재정의 하였다.
### 하지만 아래와 같은 오류가 발생하게 된다.
#### Exception in thread "main" java.lang.Error: Unresolved compilation problem:

#### The return type is incompatible with Calculator.avg()
#### 메소드의 리턴 타입이 부모 클래스의 리턴 타입과 호환되지 않는다.
### overriding을 하기 위해서는 메소드의 리턴 형식이 같아야 한다.
### 상위 클래스와 하위 클래스의 리턴 타입이 다르기에 에러가 발생하게 된다.
### 그래서 다음과 같은 조건을 충족시켜야 한다.
- 메소드의 이름
- 메소드 매개변수의 숫자와 데이터 타입 그리고 순서
- 메소드의 리턴 타입
### 위와 같이 메소드의 형태를 정의하는 사항들을 통털어서 메소드의 서명(signature)라고 한다.
### 즉 위의 에러는 메소드들 간의 서명이 달라서 발생한 문제다.
### 이 문제를 해결하는 방법은 상위 클래스의 avg와 하위 클래스의 avg 내용을 똑같이 맞추되, 하위 클래스에서 super를 활용하면 에러가 발생하지 않는다.(super는 중복 제거를 위해 사용)
### 상위 클래스 :
    public void avg() {
        System.out.println((this.left + this.right) / 2);
    }
->

    public int avg() {
        return ((this.left + this.right) / 2);
    }
---
### 하위 클래스 : 
    public int avg() {
        return ((this.left + this.right) / 2);
    }
->

    public int avg() {
        return super.avg();
    }