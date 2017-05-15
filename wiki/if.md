# 조건문 if, 그리고 switch/case
## 1. 기본 if
if는 조건식을 기준으로 참과 거짓을 판별해 각각에 설정해 놓은 코드를 실행시키는 역할을 한다. 실행의 흐름에서 분기의 역할을 하는 것이다.

```java

int a = 1;
int b = 2;

if(a > b) {
System.out.println("a가 b보다 큽니다.");
} else {
Syste.out.println("b가 a보다 큽니다.");
}

```

위 코드의 결과는 아래와 같다.

```
b가 a보다 큽니다.
```

* * *
## 2. 간결한 if
간결한 if문을 사용하면 위의 코드를 간결하게 만들 수 있다.
> (조건문) ? 참일때 실행할 코드 : 거짓일때 실행할 코드;

```java

int a = 1;
int b = 2;

System.out.println((a > b) ? "a가 b보다 큽니다." : "b가 a보다 큽니다.");
```

이렇듯이 5줄이었던 위의 코드와 비교해 1줄이면 동일한 결과값을 얻을 수 있다.

* * *
## 3. else if
else if문은 기본적으로 if문과 같지만 조금 더 상세하게 분기문을 만들 수 있다.
```java
int a = 1;

if (a == 1) {
	System.out.println("a는 1입니다.");
} else if (a == 2) {
	System.out.println("a는 2입니다.");
} else if (a == 3) {
	System.out.println("a는 3입니다.");
} else {
	System.out.println("a는 4입니다.");
}
```
위의 코드는 가장 위의 조건값에 참으로 부합함으로 첫번째 중괄호 안의 코드를 실행시킨다. 결과값은 아래와 같다.
```
a는 1입니다.
```

* * *
## 4. switch/case 문
switch/case문을 사용하면 위에서 else if문을 설명하기 위해 작성했던 코드보다 깔끔하게 작성할 수 있다. 물론 결과는 동일하다.
```java
int a = 1;

switch (a) {
	// a의 값이 1일때 실행
	case 1 : System.out.println("a는 1입니다.");
	break;

	// a의 값이 2일때 실행
	case 2 : System.out.println("a는 2입니다.");
	break;

	// a의 값이 3일때 실행
	case 3 : System.out.println("a는 3입니다.");
	break;

	// a의 값이 4일때 실행
	default : System.out.println("a는 4입니다.");
	break;
}
```
결과는 아래와 같다.
```
a는 1입니다.
```
a의 값과 같은 case문을 실행시키며, 아무 값도 해당하지 않으면 default 라인을 실행하게 된다.

그리고 case마다 break를 걸어줘야 한다. 만약 위의 소스코드에서 case 1부분에서 break를 빼면 어떤 결과가 나오게 될까?
```
a는 1입니다.
a는 2입니다.
```
break를 빼버리면 코드 실행이 주르륵 흘러내리게 된다. 그러면 원하는 결과값을 얻을 수 없으니 반드시 break를 챙기도록 하자. ~코딩할 때 정줄도 좀 챙기고..._-;;~
