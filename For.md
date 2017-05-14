# for문과  향상된 for문
## 1. for문
for문은 일정한 규칙에 의해 반복해서 코드를 실행시킬 때 사용한다.
```java
// 배열에 값 입력하고 출력하기
int[] a = new int[5];


// for (변수타입 시작값 ; 조건값 ; 증감값) { 내용 }
for (int i = 0 ; i < 10 ; i++) {
	a[i] = i;
	System.out.println(a[i]);	
}
```
위 코드의 for문은 총 10회 반복해서 실행되며, a[0] = 0 ~ a[9] = 9까지 값이 입력 됨과 동시에 그 값을 출력합니다.

```
// for문 결과값
0
1
2
3
4
5
6
7
8
9
```

* * *
## 2. 향상된 for문
향상된 for문은 배열과 관련된 반복에 사용하면 효과적이다.
```java
String a[] = {"ab", "cd", "ef", "gh"};

// 향상된 for문
// for (변수타입 유닛 : 배열명) { 내용 }
for (String item : a) {
	System.out.println (item);
}
```
코드는 짧고 효율적으로 사용하려 할수록 실력이 오른다는 이야기가 있다. 위 코드의 결과는 다음과 같다.
```
// 향상된 for문 결과값
ab
cd
ef
gh
```