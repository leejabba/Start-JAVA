# 기억해두면 유용한 클래스의 속성 정리
참조형 데이터타입(클래스)을 이용해 인스턴스를 만든 후 클래스의 속성을 이용할 수 있다. 속성은 메소드를 활용하는 것과 같다고 생각한다. 

아래에 기록할 내용은 우리가 직접 만드는 클래스의 메소드를 활용하는 것이 아닌, java의 내장 클래스에서 미리 설정되어 있는 메소드 속성에 대한 것이다. 이런 속성 값들은 잘 활용하면 코드의 성능을 높일 수 있기 때문이다.

* * * 

## 1. String
문자열을 처리하는 String 클래스(?)를 더욱 잘 활용할 수 있는 속성들에 대해 알아보자.
- .substring(시작 인덱스, 끝 인덱스) : *글자 자르기*
- .length() : *문자열의 길이 값 추출*
- .charAt(인덱스) : *한글자만 추출하기*
- .indexOf("문자") : *글자의 위치 찾기*
- .split("문자") : *값 기준으로 그룹 나누기*
- .replace("바뀔 문자", "바꿀 문자") : *글자 치환 하기*

**[소스코드]**
```java
package com.heythisway.java.string;

public class Word {

	public static void main(String[] args) {
		
		String name = "안녕하세요";
		
		// 1. 글자 자르기 (.substring(시작, 끝))
		// 문자열의 인덱스 -> "0안1녕2하3세4요5" -> 1에서 2까지 = '녕'이 추출
		String secondWord = name.substring(1, 2); 	
		System.out.println(secondWord);
		
		// 2. 문자열 길이
		int 문자열길이 = name.length();
		System.out.println(문자열길이);
		
		// 3. 한글자만 추출하기
		char 한글자 = name.charAt(3);
		System.out.println(한글자);
		
		// 4. 글자 위치 찾기
		int 몇번째 = name.indexOf("하세");
		System.out.println(몇번째);
		
		// 5. 기준으로 그룹을 나누기
		String 두덩이[] = name.split("하");
		System.out.println(두덩이[0]);
		System.out.println(두덩이[1]);
		
		// 6. 글자 치환
		String 바뀐글 = name.replace("하", "랄랄라");
		System.out.println(바뀐글);
	}
	
}
```
위의 코드를 보고 결과값을 예상 하기 위해서는 문자열 특유의 인덱스 특성에 대해서 알아야 한다.

문자열의 인덱스는 문자의 위치와 일치하지 않다. 문자의 사이사이에 인덱스 값이 위치해 있고, 속성 파라미터의 인덱스 값은 이와 같은 문자열의 인덱스 특징을 기준하여 적용된다.
> "안녕하세요" -> "[0]안[1]녕[2]하[3]세[4]요[5]"  // [숫자]는 인덱스

**[결과값]**
```
녕
5
세
2
안녕
세요
안녕랄랄라세요
```

* * *

## 2. List
얼마의 값이 들어갈지 모르는 배열을 사용해야 할 때 유용한 List에도 알아두면 유용한 속성들이 있다.
- .add(값) : 배열에 값을 입력
- .get(인덱스) : 배열의 인덱스 위치의 값 알아내기
- .size() : 배열의 개수를 반환
- .contain(값) : 배열에 해당 값이 있는지 체크한 후 boolean 값으로 반환 (값이 존재하면 true)
- .remove(값) : 배열에 해당 값을 삭제하고 삭제여부를 boolean 값으로 반환 (삭제 했다면 true)
- .remove(인덱스) : 배열 인덱스에 있는 값을 삭제하고 삭제한 값을 반환

이중에서 가장 많이 사용하는 것은 add, get, size 정도. 이 세가지 속성에 대한 예시를 확인해보자.



**[소스코드_People클래스]**
```java
public class People {
	String name;	// 이름
	int age;	// 나이 
	String gender;	// 성별 

	// 메소드 정의
	public void printPeople(){
		System.out.println(name + "씨는 " + age + "살의 " + gender + "입니다.");
	}
}
```

People 클래스를 이용해 5명(n명) 사람의 인스턴스를 만들어 보자.



**[소스코드_Main_add로 값 입력_단순모드]**
```java
public class PeopleMain {

	public static void main(String[] args) {

		// 몇 명의 인스턴스를 생성할지 모르니 List를 활용
		List<People> arrayPeople = new ArrayList<People>();	// ArrayList의 다형성, People 오브젝트만 값으로 가질 수 있도록 제네릭 설정

		// 각 속성의 값을 입력해보자. 먼저 People 데이터 타입으로 5개의 인스턴스 생성
		People people0 = new People();
		People people1 = new People();
		People people2 = new People();
		People people3 = new People();
		People people4 = new People();

		// arrayPeople의 0번째 인덱스에 people0 인스턴스를 저장
		arrayPeople.add(people0);	
		arrayPeople.add(people1);
		arrayPeople.add(people2);
		arrayPeople.add(people3);
		arrayPeople.add(people4);
	}

}

```

코드의 효율성을 위해 위의 소스코드를 아래와 같이 바꿀 수 있다.



**[소스코드_Main_add로 값 입력_for문을 이용한 모드]**
```java
import java.util.ArrayList;

public class PeopleMain {

	public static void main(String[] args) {

		// 몇 명의 인스턴스를 생성할지 모르니 List를 활용
		List<People> arrayPeople = new ArrayList<People>();	// ArrayList의 다형성, People 오브젝트만 값으로 가질 수 있도록 제네릭 설정

		// for문을 이용해 arrayPeople의 0번째부터 4번째 인덱스에 차례로 People 데이터타입 인스턴스를 생성하면서 바로 저장
		for(int i=0 ; i<5 ; i++){
			arrayPeople.add(new People());	// arrayPeople가 이미 People 데이터타입으로 만들어졌으므로 바로 인스턴스 생성이 가능
		}
	}

}

```
이제 인스턴스의 속성 값을 입력해보도록 하자.



**[소스코드_Main_get으로 값 추출 후 속성 입력]**
```java
// .get 속성을 이용해 값을 추출
arrayPeople.get(0).name = "김씨";
arrayPeople.get(0).age = 24;
arrayPeople.get(0).gender = "남자";

arrayPeople.get(1).name = "이양";
arrayPeople.get(1).age = 34;
arrayPeople.get(1).gender = "여자";

arrayPeople.get(2).name = "서군";
arrayPeople.get(2).age = 23;
arrayPeople.get(2).gender = "남자";
			
arrayPeople.get(3).name = "한군";
arrayPeople.get(3).age = 34;
arrayPeople.get(3).gender = "남자";
			
arrayPeople.get(4).name = "김양";
arrayPeople.get(4).age = 23;
arrayPeople.get(4).gender = "여자";
```
참고로 인스턴스 값 입력을 편하게 하기 위해 for문을 이용한 Scanner 기능을 이용하면 더 좋을 듯 하다.

결과를 출력하기 위한 소스코드는 다음과 같다.




**[소스코드_Main_length로 for문을 돌려 메소드 실행]**
```java
// 코드 간소화를 위해 arrayPeople를 담을 수 있는 People 데이터타입의 변수 설정
People temp = new People();

// .length 속성을 이용해 for문의 조건식을 완성
for(int i = 0 ; i<arrayPeople.size() ; i++){
	temp = arrayPeople.get(i);
	temp.printPeople();
}
```
코드를 실행해보면 아래와 같은 결과가 나온다.




**[결과값]**
```
김씨씨는 24살의 남자입니다.
이양씨는 34살의 여자입니다.
서군씨는 23살의 남자입니다.
한군씨는 34살의 남자입니다.
김양씨는 23살의 여자입니다.
```














