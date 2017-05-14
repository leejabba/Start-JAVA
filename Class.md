# 클래스, 메소드, 그리고 인스턴스
**java는 클래스의 언어** 라고 생각해도 무리가 없다. 프로그램 실행의 중심이 되는 Main 메소드도 클래스에 속해 있을 정도로 클래스는 매우 중요하다. 
그러니 당연히 클래스를 만들고 활용하는 방법을 절대 숙지하고 있어야 한다.

* * *
## 1. 클래스 만들기
클래스는 DNA 지도라고 볼 수 있다. 그리고 사용자가 직접 정의한 데이터 타입이라고 생각해도 된다. 자바에서 기본적으로 제공하는 데이터 타입인 String, ArrayList와 같이 언제든 식별자명을 붙여서 사용할 수 있다.
클래스는 보통 속성값과 메소드를 가지고 있다.
```java
// 동물에 관련된 클래스 생성

// 접근제어자 class 클래스명 {  }
// 클래스명은 첫단어는 대문자로 시작하는 것이 프로그래머들 사이에 통용되는 법칙이다.
public class Animal {
	String name;	// 동물이름
	int legs;	// 다리 갯수


	// 동물의 이름과 다리개수를 출력하는 기능을 가진 메소드 선언

	// 접근제어자 반환타입 메소드명 (입력변수)
	public void printAnimal() {
		System.out.println("동물 이름 : " + name);
		System.out.println("다리 개수 : " + legs + "개");
		System.out.println("");
	}
}
```
* * *
## 2. 인스턴스 생성해 사용하기
접근제어자와 메소드의 반환타입과 같은 내용은 다른 쓰레드에서 확인하도록 하자.

위의 코드로 인해 Animal이라는 이름의 클래스를 만들었다. 하지만 이 클래스는 바로 사용할 수 있는 상태가 아니다. ~구슬이 서말이래도...~ 클래스를 new 키워드를 통해 인스턴스화 되지 않으면 사용할 수 없다.

애써서 만든 클래스를 이제 new를 이용해 사용해보자. 동물에는 여러가지가 있다. 호랑이와 독수리를 만들어보자.

```java
public class AnimalMain {

	public static void main(String[] args) {
		
		// 클래스 Animal 데이터 타입의 tiger 인스턴스를 생성
		Animal tiger = new Animal();
		// tiger의 속성 값 입력
		tiger.name = "호랑이";
		tiger.legs = 4;
		// tiger의 메소드 실행
		tiger.printAnimal();

		// 클래스 Animal 데이터 타입의 eagle 인스턴스를 생성
		Animal eagle = new Animal();
		// eagle의 속성 값 입력
		eagle.name = "독수리";
		eagle.legs = 2;
		// eagle의 메소드 실행
		eagle.printAnimal();

	}
}
```
String a = new String();와 동일한 개념이라고 생각하면 된다. String은 문자열을 담을 수 있는 데이터 타입이었다면, Animal은 동물의 이름과 다리 개수를 담을 수 있는 데이터 타입이라고 생각할 수 있다. 

위의 코드를 실행해보면 아래와 같은 결과가 나온다.

```
동물 이름 : 호랑이
다리 개수 : 4개

동물 이름 : 독수리
다리 개수 : 2개
```

