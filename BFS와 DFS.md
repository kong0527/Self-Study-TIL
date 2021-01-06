# BFS와 DFS 🔄

그래프 탐색의 대표적 방법인 BFS와 DFS에 대해 알아보자. 

BFS는 너비 우선 탐색으로, queue를 사용해 구현하는 방법이다.

DFS는 깊이 우선 탐색으로, stack 혹은 재귀를 사용해 구현하는 방법이다.

<br/>

<br/>

### 1. BFS (Breadth-First-Search)

BFS는 먼저 루트의 자식을 먼저 방문한다. 그 다음 루트 자식의 자식, 즉 루트에서 두 개의 간선을 거쳐서 도달할 수 있는 정점을 방문한다. 

![image](https://user-images.githubusercontent.com/64277114/103726265-d3a3d280-501b-11eb-8850-4d9f9e048726.png)

<br/>

<br/>

### 2. DFS (Depth-First-Search)

DFS는 루트의 자식 정점을 하나 방문한 다음 아래로 내려갈 수 있는 곳 까지 내려간다.

더 이상 내려갈 수가 없으면 위로 되돌아오다가 내려갈 곳이 있을 때 즉각 내려간다.

![image](https://user-images.githubusercontent.com/64277114/103736794-4456e900-5034-11eb-9d26-035e5e14a71e.png)

<br/>

<br/>

마침 BOJ에 BFS와 DFS의 대표격인 [문제](https://www.acmicpc.net/problem/1260)가 있어서 풀어보았다.

🌟 BFS

```java
public static void bfs(int start) {     
    Queue<Integer> queue = new LinkedList<Integer>();
    // 문제에서 시작점이 주어졌으므로 시작점을 먼저 queue에 넣는다.
    queue.add(start);
    visited[start] = true; // 방문한 곳은 꼭 표시해주기!

    while (!queue.isEmpty()) {
        int out = queue.poll(); // queue에 들어있는 원소를 빼낸 후 출력
        System.out.print(out + " ");

        for (int i = 0; i <= vertex; i++) {
            if (graph[out][i] == 1 && visited[i] == false) {
                queue.add(i); // 간선이 연결되어 있고 아직 방문하지 않은 곳을 queue에 넣어준다.
                visited[i] = true; // queue에 넣어주었으므로 방문해주었다고 체크.
            }
        }
        // 이 for문이 끝나면 다시 while문 처음으로 돌아가서 queue 원소를 빼내고 출력 후 반복
    }
}
```

<br/>

🌟 DFS - 재귀로 구현

```java
public static void dfs(int start) {
    visited[start] = true; // parameter로 들어온 현재 위치 값을 방문했다고 체크
    System.out.print(start + " "); // 방문한 곳은 출력해준다.
    for (int i = 1; i <= vertex; i++) {
        if (graph[start][i] == 1 && visited[i] == false) {
            dfs(i); // 간선이 연결되어 있고 아직 방문하지 않은 곳을 재귀호출 -> 계속 깊이 들어감
        }
    }
}
```

<br/>

<br/>

✔ 같은 [문제](acmicpc.net/problem/2583)를 각각 [BFS](https://blog.naver.com/o____ri/222072947774)와 [DFS](https://blog.naver.com/o____ri/222072925369)로 풀어보았다.