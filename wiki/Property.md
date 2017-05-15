# 기억해두면 유용한 클래스의 속성 정리
참조형 데이터타입(클래스)을 이용해 인스턴스를 만든 후 클래스의 속성을 이용할 수 있다. 속성은 메소드를 활용하는 것과 같은 것 같다. 

아래에 기록할 내용은 우리가 직접 만드는 클래스의 메소드를 활용하는 것이 아닌 java의 내장 클래스에서 미리 설정되어 있는 메소드 속성에 대한 것이다. 이런 속성 값들은 잘 활용하면 코드의 성능을 높일 수 있기 때문이다.

* * * 

## 1. String
문자열을 처리하는 String 클래스(?)를 더욱 잘 활용할 수 있는 속성들에 대해 알아보자.
- 글자 자르기 : .substring(시작 인덱스, 끝 인덱스)
- 문자열의 길이 값 추출 : .length()
- 한글자만 추출하기 : .charAt(인덱스)
- 글자의 위치 찾기 : .indexOf("문자")
- 값 기준으로 그룹 나누기 : .split("문자")
- 글자 치환 하기 : .replace("바뀔 문자", "바꿀 문자")

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

