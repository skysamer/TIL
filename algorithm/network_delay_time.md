## ๐ก ๋คํธ์ํฌ ๋๋ ์ด ํ์
k๋ถํฐ ์ถ๋ฐํด ๋ชจ๋  ๋ธ๋๊ฐ ์ ํธ๋ฅผ ๋ฐ์ ์ ์๋ ์๊ฐ์ ๊ณ์ฐํ๋ ๋ฌธ์ ๋ค.
๋ถ๊ฐ๋ฅํ  ๊ฒฝ์ฐ -1์ ๋ฆฌํดํ๋ค.
์๋ ฅ๊ฐ(u, v, w)๋ ๊ฐ๊ฐ ์ถ๋ฐ์ง, ๋์ฐฉ์ง, ์์ ์๊ฐ์ผ๋ก ๊ตฌ์ฑ๋๋ฉฐ, ์ ์ฒด ๋ธ๋์ ๊ฐ์๋ n์ผ๋ก ์๋ ฅ๋ฐ๋๋ค.

Example 1:
Input: times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
Output: 2

Example 2:
Input: times = [[1,2,1]], n = 2, k = 1
Output: 1

Example 3:
Input: times = [[1,2,1]], n = 2, k = 2
Output: -1

์ฐ์ ์์ํ ๊ฐ์ฒด๋ฅผ ํ์ฉํ์ฌ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํ๋ค.
~~~java
public class Solution {
    public int networkDelayTime(int[][] times, int n, int k) {
        if(times==null || times.length==0 || times[0].length==0){
            return -1;
        }

        // ํ๊ณผ ์ด์ ๊ฐ๊ฐ ์ถ๋ฐ์ง, ๋์ฐฉ์ง ๋ธ๋๋ฅผ ์ค์ ํ๊ณ  ํด๋นํ๋ ๊ฐ์ ํต๊ณผ์๊ฐ์ ์ฝ์
        int[][] grid=new int[n+1][n+1];

        for(int[] arr : grid){
            Arrays.fill(arr, Integer.MAX_VALUE);
        }

        // grid์ ํ : ์ถ๋ฐ ๋ธ๋
        // grid์ ์ด : ๋์ฐฉ ๋ธ๋
        // grid์ ๊ฐ ์ธ๋ฑ์ค์ ๊ฐ : ์ถ๋ฐ๋ธ๋ -> ๋์ฐฉ๋ธ๋ ๊น์ง์ ๊ฑธ๋ฆฌ๋ ์๊ฐ
        // grid์ ๊ฐ ์ธ๋ฑ์ค์ int ์ต๋๊ฐ์ด ๋ค์ด์๋ค๋ฉด garbage data
        for(int[] curEdge : times){
            grid[curEdge[0]][curEdge[1]]=curEdge[2];
        }

        // ์ธ๋ฑ์ค ๋ณ๋ก ํต๊ณผ ์๊ฐ์ ์ ์ฅํ๋ ๋ฐฐ์ด
        // 0๋ฒ์งธ ์ธ๋ฑ์ค๋ ์ฌ์ฉํ์ง ์์(0 ๋ธ๋๋ ์๊ธฐ ๋๋ฌธ)
        int[] res=new int[n+1];
        Arrays.fill(res, Integer.MAX_VALUE);

        // ์ถ๋ฐ ๋ธ๋๊ฐ ๊ฐ์ ๋์ฐฉ ๋ธ๋๋ฅผ ์ฐ์ ์์์ ๋ฐ๋ผ ์ ๋ ฌ ํ๊ธฐ ์ํด ์ฐ์ ์์ ํ ์ฌ์ฉ(ex: [2,1], [2,3])
        PriorityQueue<Integer> minHeap=new PriorityQueue<Integer>(n, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return res[o1]-res[o2];
            }
        });

        // ์์ ๋ธ๋ ์ฝ์
        minHeap.offer(k);
        res[k]=0;

        // ์ถ๋ฐ ๋ธ๋๋ฅผ ๊ธฐ์ ์ผ๋ก ๋์ฐฉํ  ์ ์๋ ๋ชจ๋  ๋ธ๋ ์ง์ ์ ํ์
        // ์ถ๋ฐ ๋ธ๋์ ์ฐ๊ฒฐ๋๋ ๋์ฐฉ ๋ธ๋๊ฐ ์กด์ฌํ  ๊ฒฝ์ฐ, ๋ค์ ๊ทธ ๋ธ๋๋ฅผ ๊ธฐ์ ์ผ๋ก ๋ชจ๋  ๋ธ๋๋ฅผ ํ์
        while(!minHeap.isEmpty()){
            Integer start=minHeap.poll();

            for(int i=1; i<=n; i++){
                // ๋ธ๋ ํต๊ณผ ์๊ฐ
                int curWeight=grid[start][i];

                if(curWeight!=Integer.MAX_VALUE && res[i] > res[start]+curWeight){
                    // ์ถ๋ฐ ๋ธ๋๋ฅผ ๋์ฐฉํ๋๋ฐ ๊ฑธ๋ฆฐ ์๊ฐ + ๋ชฉ์ ์ง ๋ธ๋๋ฅผ ๋์ฐฉํ๋๋ฐ ๊ฑธ๋ฆฐ ์๊ฐ
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
