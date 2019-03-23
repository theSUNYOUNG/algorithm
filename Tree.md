
세그먼트 알고리즘
-
->주어진 쿼리에 대해 빠르게 응답하기 위해 만들어진 자료구조 
 
주어진 배열의 구간들을 표현하는 이진트리를 만든다. 구간트리의 루트는 항상 배열의 전체구간 [0~N-1] 이며, 한트리는 왼쪽 자식, 다른 쪽은 오른쪽 자식을 나타낸다.

시간 복잡도는 O(logN)

알고리즘 기본 틀
-
초기화 해주는 부분으로 이진트리를 만드는 부분

	static long init(int[] arr, int start, int end, int node) {
		if(start==end){
			return treeArr[node] = arr[start];
		}
		int mid = (start+end)/2;
		
		return treeArr[node]=init(arr,start,mid,node*2) + init(arr,mid+1,end,node*2+1);
	}

업데이트 하는 부분
만약 한 노트의 숫자를 증가 시키고 싶으면. 그 노드에 연결 되어 있는 모든 부모들의 숫자도 같이 증가 시켜야 한다.
그렇기 때문에 만약 2->4로 변경 하고 싶으면 연결 되어 있는 노드에 모드 +2를 증가 시켜야 한다 (4-2)

    static void update(int node, int start, int end, int index, long diff){
    		if(!(start<=index && end >= index))
    			return;
    		treeArr[node] += diff;
    		if(start != end){
    			int mid = (start + end) / 2;
    			update(node*2, start, mid, index, diff);
    			update(node*2+1, mid+1, end, index, diff);
    		}
    	}

일정 구간을 합치는 부분
구간을 벗어나면 리턴0
자식 노드가 없는 경우 or 구하려는 값이 모두 포함되는 경우 현재 트리의 노드값 리턴
구하려는 구간이 현재의 범위보다 작은경우 더 뒤져본다.

    static long sum(int node, int start, int end, int left, int right){
    		if(left > end || right < start){
    			return 0;
    		}
    		if(left <= start && end <= right){
    			return treeArr[node];
    		}
    		int mid=(start+end)/2;
    		return sum(node*2,start,mid,left,right)+sum(node*2+1,mid+1,end,left,right);
    	}
 
[백준1068 트리](https://gist.github.com/theSUNYOUNG/82ac7d44cf5f8e673dee2e95b6ed90c9)  
[백준 1991 트리순회](https://gist.github.com/theSUNYOUNG/cea0c9cb2e1196eca64f68a5196db745)  
[백준 2042 구간 합 구하기](https://gist.github.com/theSUNYOUNG/0800c0b445c99784f5db4647873bb578)  
[백준 10868 최솟값](https://gist.github.com/theSUNYOUNG/44ce8c9348d9f11a480854bd8949ff23)  
[백준 2357 최솟값과 최댓값](https://gist.github.com/theSUNYOUNG/6aa2c9d0c3b4dc213634ed1f71a0037e)  

