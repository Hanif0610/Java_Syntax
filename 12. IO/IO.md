# IO(Input Output)
### IO는 말 그대로 입력과 출력을 의미한다.
### 일상생활에서 입력에는 키보드, 마우스 등이 있고, 출력에는 모니터나 스피커 등이 존재한다.
## String[] args
### String[] args는
public static void main(String[] args) {

    System.out.println(args.length);
}
### 이 중에서 main뒤 소괄호 안에 존재하는데, 이는 흔히 문자열을 담을 수 있는 배열이라 칭한다.
### 그리고 이 String[] args는 main이라는 메소드의 파라미터라고 한다.
### 여기서 파라미터는 메소드로 들어오는 입력값을 의미한다.
### 또한 main앞에 void가 붙는 것은 이 main이라는 메소드는 출력값이 존재하지 않는다는 것을 의미한다.
### 콘솔에서 입력을 받은 뒤 그걸로 eclipse에서 실행이 가능하다.
1. cmd창을 킨다.
2. class파일이 있는 최상위파일을 찾는다.(bin과 src파일이 같이 있는 곳)
3. java -cp bin 본인클래스이름.파일명
- ex) java -cp bin study.InputOutput
### 이것을 입력한 후 스페이스바를 누른 뒤에 숫자나 영문자를 입력하면 그 값이 출력이 될 것이다.
### 이렇게 입력한 값은 String[] args의 인자로 들어간 후 eclipse에서 실행해보면 들어있는 길이를 출력하게 된다.
public static void main(String[] args) {

    for(String e : args){
        System.out.println(e);
    }
}
### 만약 위 코드로 설계를 한다면, args에 들어온 인자를 e에 하나씩 꺼내어 담고, 그것을 출력하는 형태로 된다.
### 콘솔로 one two three라고 입력을 한다.
### 좌측 위에 run버튼의 화살표 -> Run Configurations -> 좌측 위에 파일 추가 버튼 클릭 -> Name을 입력 -> Arguments -> Program arguments에 one two three입력
### 여기서 각각의 인자는 띄어쓰기로 구분한다. 그러면 각각의 인자가 코드로 옮겨진다.
### 그럼 eclipse에서 실행할 때도 one two three라고 나오게 된다.
---
## Scanner
### 코드가 실행 도중에도 입력을 받을 수 있다.
public static void main(String[] args) {

    Scanner sc = new Scanner(System.in); //새로운 인스턴스 생성
    int i = sc.nextInt();
    System.out.println(i*1000);
    sc.close();
}
### 사용하기에 앞서 scanner를 사용할려면 import를 해야 사용할 수 있다.
### import java.util.Scanner;를 통하여 scanner를 사용할 수 있게된다.
### 현재 윗 코드는 new Scanner(System.in)라는 것을 sc라는 변수에 담았다.
### 그리고 i라는 int형 변수에 입력값을 받겠다고 하였다.
### i의 자료형이 int이기 때문에 문자형을 입력하면 에러가 발생하게 된다.
### 그리고 입력값*1000을 하여 연산 결과가 화면에 출력된다.
### 또한 입력을 한번만 입력받는 것이 아닌, 연속적으로 입력을 받을 수 있다.
public static void main(String[] args) {

    Scanner sc = new Scanner(System.in);
    while(sc.hasNextInt()) { //숫자가 들어오면 계속 반복(숫자가 아닌게 입력되면 자동 종료)
        System.out.println(sc.nextInt()*1000); 
    }
    sc.close();
}
### while이라는 반복문을 통하여 자료형이 int인 값이 들어올때마다 화면에 출력한 후 다시 입력을 받는다.
### 단, 숫자가 아닌 문자열이 들어오게 된다면 화면에 출력하지 않고 즉시 종료시킨다.
### 그리고 파일에 입력돼있는 것을 코드로 불러와 화면에 출력할 수도 있다.
public static void main(String[] args) {
    
	try {
        File file = new File("out.txt");
        Scanner sc = new Scanner(file);
        while(sc.hasNextInt()) { //파일에 저장된 것이 숫자면 실팽
            System.out.println(sc.nextInt()*1000); 
        }
        sc.close();
    } catch(FileNotFoundException e){ //예외처리(파일을 찾을 수 없으면 에러메시지를 출력)
        e.printStackTrace();
    }
}
### 일단 자바 소스가 있는 파일, bin과 src가 있는 파일에 메모장을 하나 만들어야 한다.
### 여기서 try와 catch는 예외처리라고 하여, 파일을 찾을 수 없는겨우 catch로 넘어가지만, 파일을 찾을 수 있을 때는 try문을 실행하게 된다.
### file은 "out.txt"라는 메모장 파일을 가리켜 그 안에 있는 내용을 입력값으로 가져온다.
### 그리고 이 file이란 변수를 Scanner변수 sc에 담아서 파일에 있는 내용을 불러온다.
### 메모장 안에 있는 내용이 숫자면 실행하고, 문자면 그대로 나가게된다.