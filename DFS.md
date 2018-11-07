# DFS  

### 문제 종류
#### 1.행렬을 만들어서 동서남북을 뒤지며 일정한 곳까지 이동하기  
#### 2.list 형식으로 값이 주어지고, 시작점 끝점까지 이동하는 경로 찾기  
####  

***  

**기본 DFS 경로 찾는 방법을 공부해 보자**  
#### 노선 정보가 주어 지게 되고, DFS를 사용 하여 경로 찾기를 해볼것이다. 처음은 1부터 끝까지 찾는 방법. 두번째는 1부터 특정한 곳까지 갈 수 있는 모든 정보를 출력해 볼것이다.
> 입력 값 (시작 값은 무조건 1)  
>> 5 //정점의 갯수  
>> 4 end //값  
>> 7 입력 //값의 갯수   
>> 1 2  
>> 1 3  
>> 2 3  
>> 2 5  
>> 3 4  
>> 3 5  
>> 4 5  

1.Main 작성  
```
static int[][] map;
	static boolean[] visited;
	static int N,end,input;
	static Stack<Integer> s=new Stack<Integer>();
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		N=sc.nextInt(); //5
		end=sc.nextInt(); //4
		input=sc.nextInt();
		
		map=new int[N+1][N+1];
		visited=new boolean[N+1];
		for(int i=0; i<input; i++){
			int x=sc.nextInt();
			int y=sc.nextInt();
			map[x][y]=map[y][x]=1;
		}
		
		DFS(1);
```
2.DFS 작성  
시작점 1부터 최대값인 5까지 가는 방법만 조사한다. 

```
private static void DFS(int v) {
		//DFS 구현
		visited[v]=true;
		System.out.print(v+" ");
		
		for(int i=0; i<N+1; i++){
			if(map[v][i]==1 && visited[i]==false){
				//노드가 이어져 있고, 방문을 하지 않았다면 진행
				DFS(i);
			}
		}
	}
```

if 특정 지점까지 가는 방법은?  
1부터 4까지 갈 수 있는 방법 모두를 찾아보자! 
```
private static void DFS(int v) {
		//DFS 구현
		visited[v]=true; // 방문한 곳을 체크해 준다.
		s.push(v); // stack에 값 넣어 주기 (지나온 경로 넣어주기)
		if(v==end){
			int size=s.size();
			
			for(int k=0; k<size; k++){
				System.out.print(s.elementAt(k));
			}System.out.println();
			s.pop();//DFS에서 빠져 나올땐 pop
			return;
		}
		for(int i=0; i<N+1; i++){
			if(map[v][i]==1 && visited[i]==false){
				//노드가 이어져 있고, 방문을 하지 않았다면 진행
				DFS(i);
				visited[i]=false;//DFS에서 빠져나올때 
			}
		}
		s.pop(); //DFS에서 빠져나올때 
	}
  ```
      
***
## 문제를 풀어보자!!  

시작점에서 끝점으로 가는 모든 경로 노선 찾기 - 필수  
[DFS모든경로찾기](https://gist.github.com/theSUNYOUNG/09deb3e28e27aa11791586a39edbe123)  
[백준-7576 토마토](https://gist.github.com/theSUNYOUNG/9b554837a2c084af073b0e7c7d8b7da6)  
[백준-7569 토마토](https://gist.github.com/theSUNYOUNG/f4827e74fb0bbdcd65841d88eb0a0c5f)  
[백준-1987 알파벳](https://gist.github.com/theSUNYOUNG/718e8dca106803c123412f8ae77c0244)  
[백준-2146 다리만들기](https://gist.github.com/theSUNYOUNG/a38fe939c914ca3f956a63d2a45b1d76)  
[백준-2178 미로탐색](https://gist.github.com/theSUNYOUNG/804eeac17d3007a0a51e62f943b439a8)  
[백트래킹]  

    
[정올-1840 치즈](https://gist.github.com/theSUNYOUNG/6c3bb3b1f747b69ada107c539b26c788)  
[백준-1890 점프](https://gist.github.com/theSUNYOUNG/e6dcc9d0a04f4b861a554005d059f399)  
[백준-1987 알파벳](https://gist.github.com/theSUNYOUNG/a26c6854708ea40ab26f26bb28e26005)  

[정올 1681 해밀턴 순환회로](https://gist.github.com/theSUNYOUNG/d3e7e5868af299b42fb5d2b8b5a9db25)  
[특정문자 찾기](https://gist.github.com/theSUNYOUNG/d1852e06cf8f06cf412d7b50febf3513)  
[형렬의 모든 조합 중 최대합,](https://gist.github.com/theSUNYOUNG/e66846967d85a94296eb82314c1accca)  

[백준 1759 암호만들기](https://gist.github.com/theSUNYOUNG/367839437706da3490d58b5351520545)복습!  
[백준 10819 차이를 최대로](https://gist.github.com/theSUNYOUNG/0b503f6763b6b91bcce564d234e5f351)모든 조합 만들기!! 로또랑비슷!복습!  
[백준 2661 좋은수열](https://gist.github.com/theSUNYOUNG/aeeeb391fd55745f46fd265df0f182f8) 모든조합!!    
[백준 2529 부등호](https://gist.github.com/theSUNYOUNG/dfa53ac60417b052929bc0f478872d25) 모든조합인데, 최대 최소값 찾기.   
[정올 벽장문이동](https://gist.github.com/theSUNYOUNG/690c5be624516a1b105b5b9cb28e55d7)  
[백준 14888 연산자 끼워넣기](https://gist.github.com/theSUNYOUNG/5de2e9a245a187690636cbc971b4d556) 부등호랑 비슷  
[백준 14502 연구소](https://gist.github.com/theSUNYOUNG/3287d6b114091b5199e790be8fc63165)   
[백준 소문난 칠공주](https://gist.github.com/theSUNYOUNG/ffb7c472ca2fb786d7a39e79700e5c58)  



여러 케이스 DFS 문제들 
