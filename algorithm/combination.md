## ๐ก ์กฐํฉ
์ ์ฒด ์ n๊ฐ๋ฅผ ์๋ ฅ๋ฐ์ k๊ฐ์ ์กฐํฉ์ ๋ฐํํ๋ ๋ฌธ์ ๋ค.

Example 1:

Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]

Example 2:

Input: n = 1, k = 1
Output: [[1]]

์ญ์ ๋ฐฑํธ๋ํน์ ์ด์ฉํ์ฌ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํ๋ค.
~~~java

public class Solution {
    public List<List<Integer>> result=new ArrayList<>();
    public boolean[] visited;

    public List<List<Integer>> combine(int n, int k) {
        int element=1;
        int[] nums=new int[n];
        visited=new boolean[n];

        for(int i=0; i<n; i++){
            nums[i]=element++;
        }

        recursion(k, nums, new ArrayList<>(), 0);
        System.out.println(result.toString());
        return result;
    }

    public void recursion(int size, int[] nums, List<Integer> combinations, int start){
        if(combinations.size()==size){
            result.add(new ArrayList<>(combinations));
            return;
        }

        for(int i=start; i<nums.length; i++){
            combinations.add(nums[i]);
            recursion(size, nums, combinations, ++start);

            combinations.remove(combinations.size()-1);
        }
    }
}
~~~

-----
</br>
