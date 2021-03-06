#위상정렬

위상정렬은 어떤 순서를 정렬할때 사용하는 알고리즘이다. 
답은 정해진 1가지가 아닌 여러개가 될 수 있고, 순환이면 위상정렬의 조건을 만족할 수 없다! 

1. 진입차수가 0인 정점을 큐에 삽입한다
2. 큐에서 원소를 꺼내 연결된 모든 간선을 제거한다
3. 간선 제거 이후 진입차수가 0이된 정점을 큐에 삽입한다
4. 큐가 빌때 까지 2~3을 반복한다. 
모든 원소를 방문하기 전에 큐에 빈다면 사이클이 존재 한다는것, 
모든 원소를 방문했다면 큐에서 꺼낸 순서가 위상정렬의 결과이다.

[백준 2252 줄세우기](https://gist.github.com/theSUNYOUNG/2cd746f3085227a692b17a3cf2f48aac)  
[백준 2623 음악프로그램](https://gist.github.com/theSUNYOUNG/3a8c9c9c024ecd757720ce885c2d04f0)  
[백준 1766 문제집](https://gist.github.com/theSUNYOUNG/19d1d0a0a56a26bdbd196db527e87d29)쉬운 문제를 먼저 풀어야 하기 때문에 우선순위 큐(PriorityQueue)를 이용하여 처리 
[백준1005 ACM Craft](https://gist.github.com/theSUNYOUNG/fd66c9052264c8ed6c2a9b22cb9cac42) ** 순서대로 진행 하면서 걸리는 최소한의 시간을 계산   
