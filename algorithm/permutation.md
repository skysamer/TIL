## 💡 순열
서로 다른 정수를 입력받아 가능한 모든 순열을 추출하는 문제다.

Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

Example 2:

Input: nums = [0,1]
Output: [[0,1],[1,0]]

Example 3:

Input: nums = [1]
Output: [[1]]

백트래킹을 이용하여 문제를 해결했다.
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
            if(visited[i]) { continue; } // 사용한 숫자는 건너뛰기

            visited[i]=true;
            list.add(nums[i]);

            /**
             * nums의 각 인덱스 별로 재귀를 호출함(nums의 길이가 3인 경우 재귀를 3번 호출)
             * list에 원소를 하나 넣을때마다 재귀를 호출하여 nums 배열을 처음부터 다시 순회
             * */
            backTracking(list, nums);

            list.remove(list.size()-1); // list에 들어간 원소의 역순으로 삭제
            visited[i]=false;
        }

    }
}

~~~

-----
</br>
