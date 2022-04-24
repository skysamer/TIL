## 💡 K 경유지 내 가장 저렴한 항공권
시작점에서 도착점까지의 가장 저렴한 가격을 계산하되, K개의 경유지 이내에 도착하는 가격을 리턴하는 문제다.
경로가 존재하지 않을 경우 -1을 리턴한다.

Example 1:
Input: n = 3, flights = [[0,1,100],[1,2,100],[0,2,500]], src = 0, dst = 2, k = 0
Output: 500

시작점 src 노드 0에서 도착점 dst 노드 2까지 최저가는 0->1->2 경로인 200이지만, 경유지가 하나도 없어야 하므로(k=0)
이 조건을 만족시키는 최저가는 0->2인 500이다.

우선순위큐 객체를 활용하여 문제를 해결했다.
~~~java
public class Solution {
    public int findCheapestPrice(int n, int[][] flights, int src, int dst, int k) {
        int[] prices=new int[n]; // 배열의 각 index는 노드 번호
        Arrays.fill(prices, Integer.MAX_VALUE);
        prices[src]=0;

        // 경유지 횟수+1 만큼 반복문 순회
        for(int i=0; i<=k; i++){
            int[] temp=Arrays.copyOf(prices, n);

            // 항공권 출발지-도착지 별 가격 검색
            for(int[] flight : flights){
                int start=flight[0];
                int next= flight[1];
                int price=flight[2];

                if(prices[start]==Integer.MAX_VALUE){
                    continue;
                }
                temp[next]=Math.min(temp[next], prices[start]+price);
            }
            prices=temp;
        }
        return prices[dst] == Integer.MAX_VALUE ? -1 : prices[dst];
    }

}
~~~

-----
</br>
