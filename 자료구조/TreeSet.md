## TreeSet

#### TreeSet이란?

Set 인터페이스를 구현한 클래스로, HashSet처럼 중복 데이터를 저장하지 않는다는 성질을 가진다.

하지만 HashSet과 달리 Red-Black Tree로 구현되어 있어 검색, 정렬에 높은 성능을 보인다.

<br/>

**❓ 레드 블랙 트리**

![image](https://user-images.githubusercontent.com/64277114/174934387-92d5a3ab-5f43-4b63-b558-fbb2ca72bb10.png)

* 모든 노드는 빨간색 혹은 검은색이다
* 루트 노드는 검은색이다.
* 모든 리프 노드(NIL)들은 검은색이다.
* 빨간색 노드의 자식은 검은색이다.

❗ 레드 블랙 트리는 부모 노드보다 작은 값을 가지는 노드는 왼쪽, 큰 값을 가지는 노드는 오른쪽으로 배치한다.

<br/>

#### TreeSet 사용

**TreeSet 선언**

```java
// 오름차순
TreeSet<Integer> ts = new TreeSet<>();

// 내림차순
TreeSet<Integer> ts = new TreeSet<>(Collections.reverseOrder());
```

<br/>

**TreeSet 값 접근**

```java
TreeSet<Integer> ts = new TreeSet<>();

// 값 추가
ts.add(1);
ts.add(3);

// 값 삭제
ts.remove(3); // 3 삭제

ts.pollFirst(); // 첫 데이터 삭제
ts.pollLast(); // 마지막 데이터 삭제

ts.first(); // ts 최솟값
ts.lst(); // ts 최댓값

ts.higher(1); // 1 보다 큰 값 중 최솟값
ts.lower(1); // 1 보다 작은 값중 최댓값
```

