## ๐ก ์์ด
์๋ก ๋ค๋ฅธ ์ ์๋ฅผ ์๋ ฅ๋ฐ์ ๊ฐ๋ฅํ ๋ชจ๋  ์์ด์ ์ถ์ถํ๋ ๋ฌธ์ ๋ค.

Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

Example 2:

Input: nums = [0,1]
Output: [[0,1],[1,0]]

Example 3:

Input: nums = [1]
Output: [[1]]

๋ฐฑํธ๋ํน์ ์ด์ฉํ์ฌ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํ๋ค.
~~~java
public class Solution {
    List<List<Integer>> result;
    boolean[] visited;
    int numCount;

    public List<List<Integer>> permute(int[] nums) {
        numCount=nums.length;
        visited=new boolean[numCount];
        result=new ArrayList<>();

        backTracking(new ArrayList<>(), nums);

        return result;
    }

    public void backTracking(List<Integer> list, int[] nums){
        if(list.size()==numCount){
            result.add(new ArrayList<>(list));
            return;
        }

        for(int i=0; i<numCount; i++){
            if(visited[i]) { continue; } // ์ฌ์ฉํ ์ซ์๋ ๊ฑด๋๋ฐ๊ธฐ

            visited[i]=true;
            list.add(nums[i]);

            /**
             * nums์ ๊ฐ ์ธ๋ฑ์ค ๋ณ๋ก ์ฌ๊ท๋ฅผ ํธ์ถํจ(nums์ ๊ธธ์ด๊ฐ 3์ธ ๊ฒฝ์ฐ ์ฌ๊ท๋ฅผ 3๋ฒ ํธ์ถ)
             * list์ ์์๋ฅผ ํ๋ ๋ฃ์๋๋ง๋ค ์ฌ๊ท๋ฅผ ํธ์ถํ์ฌ nums ๋ฐฐ์ด์ ์ฒ์๋ถํฐ ๋ค์ ์ํ
             * */
            backTracking(list, nums);

            list.remove(list.size()-1); // list์ ๋ค์ด๊ฐ ์์์ ์ญ์์ผ๋ก ์ญ์ 
            visited[i]=false;
        }

    }
}

~~~

-----
</br>
