## 💡 조합
전체 수 n개를 입력받아 kr개의 조합을 반환하는 문제다.

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

역시 백트래킹을 이용하여 문제를 해결했다.
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
