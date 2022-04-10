## 💡 네트워크 딜레이 타임
k부터 출발해 모든 노드가 신호를 받을 수 있는 시간을 계산하는 문제다.
불가능할 경우 -1을 리턴한다.
입력값(u, v, w)는 각각 출발지, 도착지, 소요 시간으로 구성되며, 전체 노드의 개수는 n으로 입력받는다.

Example 1:
Input: times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
Output: 2

Example 2:
Input: times = [[1,2,1]], n = 2, k = 1
Output: 1

Example 3:
Input: times = [[1,2,1]], n = 2, k = 2
Output: -1

우선순위큐 객체를 활용하여 문제를 해결했다.
~~~java
public class Solution {
    public int networkDelayTime(int[][] times, int n, int k) {
        if(times==null || times.length==0 || times[0].length==0){
            return -1;
        }

        // 행과 열에 각각 출발지, 도착지 노드를 설정하고 해당하는 값에 통과시간을 삽입
        int[][] grid=new int[n+1][n+1];

        for(int[] arr : grid){
            Arrays.fill(arr, Integer.MAX_VALUE);
        }

        // grid의 행 : 출발 노드
        // grid의 열 : 도착 노드
        // grid의 각 인덱스의 값 : 출발노드 -> 도착노드 까지의 걸리는 시간
        // grid의 각 인덱스에 int 최대값이 들어있다면 garbage data
        for(int[] curEdge : times){
            grid[curEdge[0]][curEdge[1]]=curEdge[2];
        }

        // 인덱스 별로 통과 시간을 저장하는 배열
        // 0번째 인덱스는 사용하지 않음(0 노드는 없기 때문)
        int[] res=new int[n+1];
        Arrays.fill(res, Integer.MAX_VALUE);

        // 출발 노드가 같은 도착 노드를 우선순위에 따라 정렬 하기 위해 우선순위 큐 사용(ex: [2,1], [2,3])
        PriorityQueue<Integer> minHeap=new PriorityQueue<Integer>(n, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return res[o1]-res[o2];
            }
        });

        // 시작 노드 삽입
        minHeap.offer(k);
        res[k]=0;

        // 출발 노드를 기점으로 도착할 수 있는 모든 노드 지점을 탐색
        // 출발 노드와 연결되는 도착 노드가 존재할 경우, 다시 그 노드를 기점으로 모든 노드를 탐색
        while(!minHeap.isEmpty()){
            Integer start=minHeap.poll();

            for(int i=1; i<=n; i++){
                // 노드 통과 시간
                int curWeight=grid[start][i];

                if(curWeight!=Integer.MAX_VALUE && res[i] > res[start]+curWeight){
                    // 출발 노드를 도착하는데 걸린 시간 + 목적지 노드를 도착하는데 걸린 시간
                    res[i]=res[start]+curWeight;
                    minHeap.offer(i);
                }

            }

        }
        int count=0;

        for(int i=1; i<=n; i++){
            if(res[i]==Integer.MAX_VALUE){
                return -1;
            }
            count=Math.max(count, res[i]);
        }
        return count;
    }
~~~

-----
</br>
