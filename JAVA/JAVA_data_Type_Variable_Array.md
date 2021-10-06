-   프리미티브 타입 종류와 값의 범위 그리고 기본 값
-   프리미티브 타입과 레퍼런스 타입
-   리터럴
-   변수 선언 및 초기화하는 방법
-   변수의 스코프와 라이프타임
-   타입 변환, 캐스팅 그리고 타입 프로모션
-   1차 및 2차 배열 선언하기
-   타입 추론, var

---
Data Type이란 해당 데이터가 메모리에 어떻게 저장되고 프로그램이 어떻게 처리되어야 하는지 명시적으로 알려주는 것이다
JAVA의 Data Type에는 크게 기본형 (Primitive Type) 과 참조형 (Reference Type) 이 있다
참조형은 참조 주소를 카리키는 데이터 타입이고
기본형은 실제 값을 갖는 데이터 타입이다

# 기본형 (Primitive) 타입 
* 8가지의 기본형 타입이 있다
* 기본 값이 있기 때문에 Null이 존재하지 않는다
	* 만약 Null을 넣고 싶다면 래퍼클래스 (Wrapper Class)를 활용한다
* 실제 값을 저장하는 `Stack` 메모리에 저장된다


## 기본형의 Wrapper Class
* 기본형타입의 객체로 사용할 때 Wrapper Class를 사용한다
* 포장객체라고도 한다
* 
### 왜 Wrapper Class를 써야 할까?
* 기본자료형을 클래스화해 클래스의 장점을 갖게 하기 위해서
```
pubilc void printEveryting (Object obj){
	System.out.println(obj)
}
```
라는 소스가 있을 경우 일반 primitive 타입은 사용이 불가능하다
인자의 자료형이 클래스인 Object기 때문에 Wrapper 클래스 없이 기본 자료형으로는 실행할 수 없기 때문이다
하지만 자바 컴파일에서 필요한 경우 Primitive 타입을 `AutoBoxing` 을 해주기 때문에 자동으로 변환시켜준다
(반대로 Wrapper 클래스에서 꺼낼 땐  Unboxing 이라고 한다)
# 참조형 (Reference) 타입
# 리터럴
# 변수
## 변수의 선언 초기화
## 변수의 스코프와 라이프타임
## 변수의 캐스팅

# 배열
# var 