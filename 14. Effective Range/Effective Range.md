# 유효범위
### 유효범위란 변수를 전역변수, 지역변수 나눠서 좀 더 관리하기 편리하도록 한 것이다.
### 프로그램이 커지면 여러 가지 이유로 이름이 충돌하게 된다.
### 이를 해결하기 위해서 고안된 것이 유효범위라는 개념이다.
> 흔히 스코프(Scope)라고도 부른다.
{
 
    static void a() {
        int i = 0;
    }
 
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            a();
            System.out.println(i);
        }
    }
}
> 0

> 1

> 2

> 3

> 4
### for문 안에서 a()라는 메소드를 호출하나, a라는 메소드에는 i값을 0으로 바꾸는 코드가 존재한다.
### 허나 a메소드의 코드는 {}(스코프)로 묶여있기에, a라는 메소드의 스코프 안에서만 유효하기에 a라는 메소드에서만 사용이 가능하다.
### 따라서 a메소드에서 i에 값을 변화하여도, main에는 적용이 되지 않는다.
### 단, class 바로 밑에서 변수를 선언한다면, 그것은 모든 메소드에 적용이 된다.
 {

    class Scope {

        static int i;
        
        static void a() {
            i = 0;
        }
    
        public static void main(String[] args) {
            for (i = 0; i < 5; i++) {
                a();
                System.out.println(i);
            }
        }
    }
 }
### 이 코드를 실행시키면 0이 무한반복 하게 된다.
### static int i;라는 것이 메소드 안에서 선언한 것이 아닌, class 바로 밑에서 선언을 하여 코드 전체에 i라는 변수에 영향을 끼치게 된다.
### 따라서 a라는 메소드를 호출했을 때, i를 0으로 바꿈으로써 main에도 적용이 되는 것이다.
### 이때, class 바로 밑에서 선언되는 변수는 어디에 속해있는 변수가 아닌, class의 직접적으로 속해있는 직속변수이다.
### 이러한 변수를 전역변수라고 한다.
### 또한 메소드 안에서 선언되는 변수를 지역변수라고 한다.
### 만약 a라는 메소드나 main에서 i라는 변수 앞에 int로 새로 만들게 된다면, 출력값은 0,1,2,3,4가 나오게 된다.
### 이는 지역변수를 생성함으로써 전역변수와 관련이 없어지게 된다.
{

    static int i = 5;
 
    static void a() {
        int i = 10;
        b();
    }
 
    static void b() {
        System.out.println(i);
    }
 
    public static void main(String[] args) {
        a();
    }
}
> 5
### 전역변수는 i에는 5라는 값이 담겨있는 상태로 시작하게 된다.
### main에서 a라는 메소드를 호출한다.
### a라는 메소드에는 int i = 10;이 존재한다.
### 이는 지역변수 i를 생성한것이기에 a라는 메소드 안에서만 유효하다.
### 또한 b라는 메소드를 호출한다.
### b라는 메소드에는 i값을 출력하는데, i를 따로 변수를 생성하지 않았기에 전역변수로 생성된 i의 값을 출력하게 된다.
## 메소드 내(b)에서 지역변수가 존재하지 않는다면 그 메소드가 소속된 클래스의 전역변수를 사용하게 된다.
## 이러한 방식을 정적 스코프(static scope) 혹은 렉시컬 스코프(lexical scope)라고도 부른다.
## 동적 스코프라는 것도 있다. 만약 메소드 b의 결과가 10이라면 메소드 b는 메소드 a의 유효범위에 소속된 것이라고 할 수 있다.
{

    class C2 {
        int v = 10;
    
        void m() {
            int v = 20;
            System.out.println(v);
        }
    }
    
    public class ScopeDemo8 {
    
        public static void main(String[] args) {
            C2 c1 = new C2();
            c1.m();
        }
    
    }
}
> 20
### m이라는 메소드에서 지역변수를 출력하는 코드이다.
### 전역변수 v보다 지역변수 v가 더 우선순위가 높기 때문에 지역변수가 출력이 된다.
### 만약 이 상황에서 전역변수를 출력하고 싶다면 this를 사용하면 된다.
{

    class C3 {
        int v = 10;
    
        void m() {
            int v = 20;
            System.out.println(this.v);
        }
    }
    
    public class ScopeDemo9 {
    
        public static void main(String[] args) {
            C3 c1 = new C3();
            c1.m();
        }
    
    }
}
> 10
### this라는 것은 새로운 인스턴스를 생성했을 때 인스턴스 자체를 의미하는 값이 된다.
### 또한 this가 붙으면 그 객체에 대한 전역의 의미를 갖게 된다.