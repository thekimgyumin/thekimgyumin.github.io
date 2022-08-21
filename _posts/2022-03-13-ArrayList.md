---
layout: post
title: ArrayList
categories: JAVA
tags: [JAVA]
---
## ArrayList란
일반 배열과 동일하게 연속된 메모리 공간을 사용하며 인덱스는 0부터 시작한다. 하지만 배열이 크기가 고정인 반면 ArrayList는 크기가 가변적으로 변한다.

내부적으로 저장이 가능한 메모리 용량이 있으며 현재 사용 중인 공간의 크기가 있다. 만약 현재 가용량 이상을 저장하려고 할 때 더 큰 공간의 메모리를 새롭게 할당한다.

### 생성
```java
import java.util.ArrayList;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<Integer> integers1 = new ArrayList<Integer>(); // <> 부분에 타입 지정(생략 가능)
        ArrayList<Integer> integers2 = new ArrayList<>(10); // ()에 초기 용량 설정(생략 가능)
        ArrayList<Integer> integers3 = new ArrayList<>(integers1); // 다른 Collection값으로 초기화
        ArrayList<Integer> integers4 = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5)); // Arrays.asList()
    }
}
```
Set이나 다른 ArrayList를 전달하면 해당 Collections의 값들로 초기화된다.

가변 인자를 전달받는 Arrays.asList()를 사용하면 기본 값들로 생성 가능하다.

### ArrayList 엘레멘트 추가/변경
ArrayList를 생성한 후 add() 메소드로 엘레멘트를 추가할 수 있다.

또한 set() 메소드로 기존에 추가된 값을 변경하는 것도 가능하다.
```java
import java.util.ArrayList;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>();
        // add() 메소드
        colors.add("Black");
        colors.add("White");
        colors.add(0, "Green");
        colors.add("Red");

        // set() 메소드
        colors.set(0, "Blue");

        System.out.println(colors);
    }
}
```
출력값 : Blue Black White Red

add()는 기본적으로 리스트의 가장 끝에 값을 추가한다.

별도로 인덱스를 지정하면 해당 인덱스에 값이 추가되고 그 인덱스부터의 값들이 1 칸씩 밀린다.

### ArrayList 엘레멘트 삭제
추가했던 값을 삭제할 때는 remove() 메소드를 호출한다.
```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>(Arrays.asList("Black", "White", "Green", "Red"));
        String removedColor = colors.remove(0);
        System.out.println("Removed color is " + removedColor);

        colors.remove("White");
        System.out.println(colors);

        colors.clear();
        colors.add(Blue)
        System.out.println(colors);
    }
}
```
출력값 : 

Removed color is Black

Green Red

Blue

삭제할 때는 엘레멘트의 인덱스를 입력하거나 엘레멘트를 직접 입력할 수 있다.

인덱스를 통해 삭제할 경우 삭제되는 엘레멘트를 리턴받을 수 있다.

값을 지움과 동시에 해당 값으로 별도의 작업이 필요한 경우 리턴을 받아서 사용하면 된다.

ArrayList 안의 내용을 전체 삭제할 때는 clear()를 호출하면 된다.

### ArrayList 전체 값 확인
ArrayList의 모든 값들을 순회해서 출력하고 싶은 경우 다양한 방법을 사용할 수 있다.
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Iterator;
import java.util.ListIterator;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>(Arrays.asList("Black", "White", "Green", "Red"));
        // for-each 활용
        for (String color : colors) {
            System.out.print(color + "  ");
        }
        System.out.println();

        // for문 활용
        for (int i = 0; i < colors.size(); ++i) {
            System.out.print(colors.get(i) + "  ");
        }
        System.out.println();

        // iterator 활용
        Iterator<String> iterator = colors.iterator();
        while (iterator.hasNext()) {
            System.out.print(iterator.next() + "  ");
        }
        System.out.println();

        // listIterator 활용
        ListIterator<String> listIterator = colors.listIterator(colors.size());
        while (listIterator.hasPrevious()) {
            System.out.print(listIterator.previous() + "  ");
        }
        System.out.println();
    }
}
```
출력값 : 
Black White Green Red
Black White Green Red
Black White Green Red
Red Green White Black

listIterator의 경우 생성 시 ArrayList의 크기를 입력해주고 역방향으로 출력할 수 있다.

그래서 역순서로 출력이 되는 것을 확인할 수 있다.

### 값 존재 유무 확인
ArrayList의 안에 값이 존재하는지 존재한다면 어느 위치에 존재하는지 알고 싶은 경우가 있다.

먼저 값이 존재하는지만 알고 싶은 경우 contains()를 사용한다.

값이 존재할 때 어느 위치에 존재하는지 알고 싶은 경우 indexOf()를 사용할 수 있다.
```java
import java.util.ArrayList;
import java.util.Arrays;

public class ArrayListTest {
    public static void main(String[] args) {
        ArrayList<String> colors = new ArrayList<>(Arrays.asList("Black", "White", "Green", "Red"));
        boolean contains = colors.contains("Black");
        System.out.println(contains);

        int index = colors.indexOf("Blue");
        System.out.println(index);

        index = colors.indexOf("Red");
        System.out.println(index);
    }
}
```
출력 : 

true

-1

3

contains()는 값이 있는 경우 true를, 값이 없는 경우 false를 리턴한다.

indexOf()는 값이 존재하는 경우 해당 엘레멘트의 인덱스를 리턴한다.

값이 존재하지 않을 경우 -1을 리턴하기 때문에 별도로 처리가 가능하다.