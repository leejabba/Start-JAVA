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
위 코드의 for문은 총 10회 반복해서 실행되며, a[0] = 0 ~ a[9] = 9까지 값이 입력 됨과 동시에 그 값을 출력한다.

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

## 2-1. 향상된 for문 실사용 예시
Head Firs Java의 예시 코드를 향상된 for문을 이용해 효과적으로 수정해보았다. 

> **[문제] 숫자 맞추기 게임**
> 이 게임은 게임 객체 한 개와 선수 객체 세 개로 구성된다. 게임 객체에서는 0과 9 사이의 난수를 발생시키고, 선수 객체 세 개는 적당한 숫자를 난수로 찍어서 그 숫자를 맞춰야한다.


**[GameLauncher.java]**
```java
public class GameLauncher {
    public static void main(String[] args) {
        GuessGame guessGame = new GuessGame();
        guessGame.startGame();
    }
}
```

**[Player.java]**
```java
public class Player {
    public int answerNumber;

    // 이하 변수는 향상된 for문을 위한 변수 
    public int answerP;
    public boolean rightAnswer;
    public int playerNumber;

    public void guess() {
        answerNumber = (int) (Math.random() * 10);
    }
}
```

**[GuessGame.java] 책 예시 버전** 
```java
public class GuessGame {
    public void startGame() {
        // 1. Player 타입 객체 3개 생성
        Player p1 = new Player();
        Player p2 = new Player();
        Player p3 = new Player();

        // 1.2 각 플레이어의 답을 담을 변수 초기화
        int answerP1 = 0;
        int answerP2 = 0;
        int answerP3 = 0;

        // 1.3 각 플레이어의 답변이 정답인지 체크하는 boolean 타입 변수 초기화
        boolean p1RightAnswer = false;
        boolean p2RightAnswer = false;
        boolean p3RightAnswer = false;

        // 2. 난수 생성(문제 출제)
        int targetNumber = (int) (Math.random() * 10);
        System.out.println("Q : 0부터 9까지의 숫자 중 제가 어떤 숫자를 떠올리고 있는지 맞춰보세요.");

        // 3. 정답자가 나올때까지 각 선수에게 답 물어보기
        while (true) {
            System.out.println("맞춰야할 숫자는 " + targetNumber + " 입니다. \n");

            // 3.1 각 플레이어들이 추측하는 메서드 호출
            p1.guess();
            p2.guess();
            p3.guess();

            // 3.2 각 플레이어들의 답변을 출력
            answerP1 = p1.answerNumber;
            System.out.println("1번 선수가 찍은 숫자 : " + answerP1);
            answerP2 = p2.answerNumber;
            System.out.println("2번 선수가 찍은 숫자 : " + answerP2);
            answerP3 = p3.answerNumber;
            System.out.println("3번 선수가 찍은 숫자 : " + answerP3);

            // 4. 결과 확인 후 정답자 출력 또는 다시 맞춰보라고 알리기
            if (answerP1 == targetNumber) {
                p1RightAnswer = true;
            }
            if (answerP2 == targetNumber) {
                p2RightAnswer = true;
            }
            if (answerP3 == targetNumber) {
                p3RightAnswer = true;
            }

            if (p1RightAnswer || p2RightAnswer || p3RightAnswer) {
                System.out.println("맞춘 선수가 있습니다.");
                System.out.println("1번 선수 : " + p1RightAnswer);
                System.out.println("2번 선수 : " + p2RightAnswer);
                System.out.println("3번 선수 : " + p3RightAnswer);
                System.out.println("게임이 종료되었습니다.");
                break;
            }
            System.out.println("다시 시도해야 합니다.");
        }
    }
}
```


**[GuessGame.java] 향상된 for문 적용 버전** 
```java
public class GuessGame {
    public void startGame() {
        // 1. Player 타입 객체 3개 생성
        List<Player> players = new ArrayList<>();
        for (int i=0 ; i < 3 ; i++) {
            players.add(new Player());
        }

        // 1.2 각 플레이어의 답을 담을 변수 초기화
        int count = 1;
        for (Player player : players) {
            player.answerP = 0;
            player.rightAnswer = false;
            player.playerNumber = count;
            count = count + 1;
        }

        // 2. 난수 생성(문제 출제)
        int targetNumber = (int) (Math.random() * 10);
        System.out.println("Q : 0부터 9까지의 숫자 중 제가 어떤 숫자를 떠올리고 있는지 맞춰보세요.");

        // 3. 정답자가 나올때까지 각 선수에게 답 물어보기
        while (true) {
            System.out.println("맞춰야할 숫자는 " + targetNumber + " 입니다. \n");

            for (Player player : players) {
                player.guess();
                player.answerP = player.answerNumber;
                System.out.println(player.playerNumber + "번 선수가 찍은 숫자 : " + player.answerP);
                if (player.answerP == targetNumber) {
                    player.rightAnswer = true;
                }
            }

            if (players.get(0).rightAnswer || players.get(1).rightAnswer || players.get(2).rightAnswer) {
                System.out.println("맞춘 선수가 있습니다.");
                System.out.println("1번 선수 : " + players.get(0).rightAnswer);
                System.out.println("2번 선수 : " + players.get(1).rightAnswer);
                System.out.println("3번 선수 : " + players.get(2).rightAnswer);
                System.out.println("게임이 종료되었습니다.");
                break;
            }
            System.out.println("다시 시도해야 합니다.");
        }
    }
}
```

**[결과값]**
```
Q : 0부터 9까지의 숫자 중 제가 어떤 숫자를 떠올리고 있는지 맞춰보세요.
맞춰야할 숫자는 1 입니다. 

1번 선수가 찍은 숫자 : 5
2번 선수가 찍은 숫자 : 6
3번 선수가 찍은 숫자 : 5
다시 시도해야 합니다.
맞춰야할 숫자는 1 입니다. 

1번 선수가 찍은 숫자 : 2
2번 선수가 찍은 숫자 : 3
3번 선수가 찍은 숫자 : 8
다시 시도해야 합니다.
맞춰야할 숫자는 1 입니다. 

1번 선수가 찍은 숫자 : 6
2번 선수가 찍은 숫자 : 1
3번 선수가 찍은 숫자 : 6
맞춘 선수가 있습니다.
1번 선수 : false
2번 선수 : true
3번 선수 : false
게임이 종료되었습니다.

Process finished with exit code 0
```
