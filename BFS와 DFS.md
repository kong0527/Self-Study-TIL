# BFS와 DFS 🔄

그래프 탐색의 대표적 방법인 BFS와 DFS에 대해 알아보자. 

BFS는 너비 우선 탐색으로, queue를 사용해 구현하는 방법이다.

DFS는 깊이 우선 탐색으로, stack을 사용해 구현하는 방법이다.

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

✔ 같은 문제를 각각 [BFS](https://blog.naver.com/o____ri/222072947774)와 [DFS](https://blog.naver.com/o____ri/222072925369)로 풀어보았다.