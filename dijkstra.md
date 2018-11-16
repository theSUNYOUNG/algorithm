##다익스트라 알고리즘의 순서는 이렇습니다.  
1. distance는 처음에 나올 수 있는 가장 큰 값으로 초기화 해줍니다.    
여기서는 Integer.MAX_VALUE 값으로 초기화 하겠습니다.  
(문제에서 100000만 이상의 값은 안나온다 하면 100001로 초기화 하셔도 됩니다.)    

2. 시작노드의 거리를 0 으로 표시합니다(자기자신까지 거리는 0이므로)  
   그리고 시작노드의 check값을 true로 바꿔줍니다. (방문 한것이므로)    
 
3. 시작노드와 연결되어 있는 노드들의 distance 값을 갱신합니다.    

4. 방문하지 않은 노드중 distance 값이 최소인 노드 min_node를 찾습니다.    

5.  min_node의 check 값을 true로 변경합니다.   
    그리고 min_node와 연결된 노드들(방문하지 않은) distance 값을 갱신합니다.  
    이때 min_node와 연결된 distance 값이   
    distance[min_node] + (min_node와 그 노드의 거리)  
    보다 큰 경우 distance값을 distance[min_node] +(min_node와 그 노드의 거리)  
    로 갱신해줍니다.    

4~5를 모든 노드를 방문할 때까지 반복합니다.    

출처: http://bumbums.tistory.com/4 [범범스의 코딩놀이터]  

[백준 최단경로 1916](https://gist.github.com/theSUNYOUNG/a15cc16960483e0a4cd4561d9aab9b00)  
[백준 파티 1238](https://gist.github.com/theSUNYOUNG/748ac9877c343508acdc47366b710231)  
