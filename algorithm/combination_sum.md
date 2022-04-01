## 💡 조합의 합
숫자 집합 candidates를 조합하여 합이 target이 되는 원소를 나열하는 문제다.
각 원소는 중복으로 나열이 가능하다.

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

역시 백트래킹을 이용하여 문제를 해결했다.
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
