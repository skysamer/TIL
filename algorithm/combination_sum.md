## ๐ก ์กฐํฉ์ ํฉ
์ซ์ ์งํฉ candidates๋ฅผ ์กฐํฉํ์ฌ ํฉ์ด target์ด ๋๋ ์์๋ฅผ ๋์ดํ๋ ๋ฌธ์ ๋ค.
๊ฐ ์์๋ ์ค๋ณต์ผ๋ก ๋์ด์ด ๊ฐ๋ฅํ๋ค.

Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.

Example 2:

Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]

Example 3:

Input: candidates = [2], target = 1
Output: []

์ญ์ ๋ฐฑํธ๋ํน์ ์ด์ฉํ์ฌ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํ๋ค.
~~~java
public class Solution {
    List<List<Integer>> result=new ArrayList<>();

    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        int comparison=0;
        int start=0;
        List<Integer> combination=new ArrayList<>();

        recursive(comparison, target, candidates, combination, start);
        return result;
    }

    public void recursive(int comparison, int target, int[] candidates, List<Integer> combination, int start){
        if(comparison==target){
            result.add(new ArrayList<>(combination));
            return;
        }
        if(comparison>target){
            return;
        }

        for(int i=start; i<candidates.length; i++){
            combination.add(candidates[i]);
            comparison+=candidates[i];
            recursive(comparison, target, candidates, combination, start);

            combination.remove(combination.size()-1);
            comparison-=candidates[i];
            start++;
        }
    }
}
~~~

-----
</br>
