# ✨JAVA 코드 실행

![jvm_and_java_run_2](../img/jvm_and_java_run_2.png)

## JAVA로 Helloworld를 실행해보기

* 'Hello world' 를 출력하는 간단한 프로그램을 만든 후 `Hello.java` 로 저장한 후 실행시켜보기
* 이 때 명령어는 다음과 같다

```shell
>javac Hello.java //컴파일
>java Hello //실행
Hello, world //실행된 결과
```

1. `.java` 소스코드를 컴파일한다

2. 컴파일 된 `.class` 코드를 실행한다 

3. JVM으로 구동을 한다

4. main클래스부터 순차적으로 실행이 되어 `Hello, world` 가 출력된다

### ✔javac의 다양한 옵션

자바 컴파일에 사용되는 javac의 옵션들

```
# javac 실행 방법
javac [옵션] [소스파일.java]

# 옵션 여러개일 때 실행 방법
 javac -cp [참조파일 경로] -encoding [인코딩셋] -d [루트디렉토리] [소스파일.java] 
```

##### 옵션 종류

* classpath (cp) 

  * 컴파일 시 필요로 하는 참조할 클래스 파일의 파일 경로를 지정gksek

    ````
    javac -classpath [참조파일 경로] [소스파일.java]
    
    javac -cp [참조파일 경로] [소스파일.java]
    ````

* d 

  * 클래스 파일을 생성할 루트 디렉토리 설정

    ````
    javac -d [루트 디렉토리] [소스파일.java]
    ````

* encoding

  * 소스 파일에 사용된 문자열 설정

    ```
    javac -encoding [인코딩셋] [소스파일.java]
    ```

* g

  * 디버깅 정보 옵션

    ```
    javac -g:none → 디버깅 정보를 생성하지 않음
    
    javac -g:line(라인정보), var(지역변수), source(소스 파일 정보)
    ```

* nowarn

  * 경고메세지를 생성하지 않음

* sourcepath

  * 소스파일의 위치 지정

## 컴파일과 실행 과정

![img_java_programming](../img/jvm_and_java_run_4.png)



![jvm_and_java_run_3](../img/jvm_and_java_run_3.png)

1. `javac` 명령어를 사용해 `.java` 를  `.class` 파일로 변환한다
	* 이 때 나오는 파일은 아직 컴퓨터가 읽을 수 없고 자바 가상 머신(JVM)이 이해할 수 있는 코드다.
2. 생성된 자바 **바이트 코드** (`.class`) 는 클래스 로더에 의해서 **JVM**으로 로드가 된다.

3. Byte Code Verifier 에서 바이트 코드를 검증한다.
4. 실행 엔진 (Execution Engine)에 의해 기계어로 해석
5. 실행 엔진에는 **Interpretor** 와 **JIT Compiler** 가 있다 선택적으로 실행을 할 수 있다
6. 변환된 바이너리 코드는 JVM의 Runtime Data Areas 영역에 저장되어 실질적인 수행이 이루어진다
7. 실행 과정 속 JVM은 필요에 따라 Thread Synchronization 과 Garbage Collection과 같은 관리작업을 수행한다

### ✔ Byte code란

* 자바 가상머신이 이해할 수 있는 언어로 변환된 자바 소스 코드
* 자바 컴파일러에 의해 변환되는 코드의 명령어 크기가 1바이트라서 **자바 바이트 코드** 라고 불리고 있다
* 자바 바이트코드의 확장자는 `.class` 이다
* 자바 바이트 코드는 자바 가상머신(JVM)만 설치되어 있으면 어떤 운영체제에서든 실행이 가능하다



# ✨JVM

* JVM은`JAVA Virtual Machine` 을 줄인 것으로 자바를 실행하기 위한 가상머신이라고 할 수 있다.
* 자바 애플리케이션은 모두 JVM에서만 실행되기 때문에 자바 애플리케이션이 실행되기 위해서는 반드시 JVM이 필요하다.
* 일반 애플리케이션든 OS만 거치고 하드웨어로 전달되지만 JAVA의 경우는 JVM을 한번 더 거치고 하드웨어에 맞게 실행시 해석(interpret)되기 때문에 속도가 느리다.
  * 하지만 **JIT컴파일러**와 최적화기술이 적용되서 속도의 격차가 줄어듦
* JAVA는  JVM과 상호작용하기 때문에 **OS와 하드웨어에 독립적**이다
  *  다른 애플리케이션은 OS와 맞붙어 있기 때문에 OS종속적이다 
     * 다른 OS에서 실행시키기 위해선 애플리케이션을 그 OS에 맞게 변경해야한다
  *  JAVA는 JVM으로 인해 다른 OS에서도 프로그램의변경없이 실행이 가능하다
  *  JVM은 해당 OS에서 실행 가능한 JVM이 필요하다 (JVM for window..)

<img src="../img/jvm_and_java_run_1.png" alt="image-20210906053408559" style="zoom: 50%;" />

## JVM의 구성

1. 자바 인터프리터
   * 자바 컴파일러에 의해 변환된 자바 바이트 코드를 읽고 해석하는 역할을 하는 것
2. 클래스 로더
   * 자바는 동적으로 클래스를 읽어오므로 프로그램이 실행중인 런타임에서야 모든 코드가 자바 가상머신과 연결된다
   * 이 때 **동적으로 클래스를 로딩**해주는 역할을 하는 것이 클래스 로더
3. JIT 컴파일러
   * Just In Time Compiler
   * 동적번역 (dynamic translation) 이라고 함
   * 프로그램이 실행중인 런타임에 자바 바이트 코드를 실제 기계어로 변환해 주는 컴파일러
   * 프로그램의 실행 속도를 향상시키기 위해 나옴
4. 가비지 컬렉터
   * JVM은 GC (garbage collector)를 이용해서 더는 사용하지 않는 메모리를 자동으로 회수한다
   * 개발자가 따로 메모리 관리를 하지 않아도 쉽게 프로그래밍을 할 수 있도록 도와준다



# ✨요약

> 자바가 동작을 할때 소스코드(.java)를 컴파일 후(javac.ece) 자바 바이트코드 (.class) 파일로 변환한다
> 변환된 파일은  JVM에 로드가 되어 JIT과 인터프리터로 실행이 된다.
> JVM은 자바 가상머신으로 OS에 독립적으로 실행할 수 있게 한다.