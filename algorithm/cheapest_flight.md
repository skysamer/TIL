## ๐ก K ๊ฒฝ์ ์ง ๋ด ๊ฐ์ฅ ์ ๋ ดํ ํญ๊ณต๊ถ
์์์ ์์ ๋์ฐฉ์ ๊น์ง์ ๊ฐ์ฅ ์ ๋ ดํ ๊ฐ๊ฒฉ์ ๊ณ์ฐํ๋, K๊ฐ์ ๊ฒฝ์ ์ง ์ด๋ด์ ๋์ฐฉํ๋ ๊ฐ๊ฒฉ์ ๋ฆฌํดํ๋ ๋ฌธ์ ๋ค.
๊ฒฝ๋ก๊ฐ ์กด์ฌํ์ง ์์ ๊ฒฝ์ฐ -1์ ๋ฆฌํดํ๋ค.

Example 1:
Input: n = 3, flights = [[0,1,100],[1,2,100],[0,2,500]], src = 0, dst = 2, k = 0
Output: 500

์์์  src ๋ธ๋ 0์์ ๋์ฐฉ์  dst ๋ธ๋ 2๊น์ง ์ต์ ๊ฐ๋ 0->1->2 ๊ฒฝ๋ก์ธ 200์ด์ง๋ง, ๊ฒฝ์ ์ง๊ฐ ํ๋๋ ์์ด์ผ ํ๋ฏ๋ก(k=0)
์ด ์กฐ๊ฑด์ ๋ง์กฑ์ํค๋ ์ต์ ๊ฐ๋ 0->2์ธ 500์ด๋ค.

๊ธฐ์กด์ ๋ค์ต์คํธ๋ผ ์๊ณ ๋ฆฌ์ฆ ๋์ ์, ๋ฒจ๋ง-ํฌ๋ ์๊ณ ๋ฆฌ์ฆ์ ํ์ฉํ๋ค.
~~~java
public class Solution {
    public int findCheapestPrice(int n, int[][] flights, int src, int dst, int k) {
        int[] prices=new int[n]; // ๋ฐฐ์ด์ ๊ฐ index๋ ๋ธ๋ ๋ฒํธ
        Arrays.fill(prices, Integer.MAX_VALUE);
        prices[src]=0;

        // ๊ฒฝ์ ์ง ํ์+1 ๋งํผ ๋ฐ๋ณต๋ฌธ ์ํ
        for(int i=0; i<=k; i++){
            int[] temp=Arrays.copyOf(prices, n);

            // ํญ๊ณต๊ถ ์ถ๋ฐ์ง-๋์ฐฉ์ง ๋ณ ๊ฐ๊ฒฉ ๊ฒ์
            for(int[] flight : flights){
                int start=flight[0];
                int next= flight[1];
                int price=flight[2];

                // ๊ฒฝ์ ์ง๊ฐ 0์ผ ๊ฒฝ์ฐ, ์ถ๋ฐ์ง-๋ชฉ์ ์ง ์งํญ ๊ฐ๊ฒฉ๋ง ์๋ฐ์ดํธ
                if(prices[start]==Integer.MAX_VALUE){
                    continue;
                }
                // ๋์ฐฉ์ง์ ์ด๋ํ๊ธฐ๊น์ง์ ๊ฐ๊ฒฉ ์ฑ์ 
                temp[next]=Math.min(temp[next], prices[start]+price);
            }
            // ๊ฒฝ์ ์ง๊ฐ 0์ธ ๊ฒฝ์ฐ๋ถํฐ ํญ๊ณต๊ถ์ ์ํํ์ฌ prices๋ฅผ ์๋ฐ์ดํธ
            prices=temp;
        }
        return prices[dst] == Integer.MAX_VALUE ? -1 : prices[dst];
    }

}
~~~

-----
</br>
