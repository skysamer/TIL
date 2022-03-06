## 💡 상위 K 빈도 요소
배열에 등장하는 빈도수를 기준으로 상위 k개 안에 들어오는 요소들을 리턴하는 문제다.

해시맵 객체를 생성하고 key에 요소를 넣고 value에 각 요소의 개수를 저장했다.
list 객체를 생성하고, value를 기준으로 key를 정렬한 다음 list에 순차적으로 삽입한다.

크기가 상위 k개인 배열을 생성하고 list의 값을 상위 k개 만큼 배열에 삽입하고 배열을 리턴한다.

~~~java
public class KElement {
	
	public static int[] topKFrequent(int[] nums, int k) {
		HashMap<Integer, Integer> map=new HashMap<>();
		
		for(int i=0; i<nums.length; i++){
			if(map.containsKey(nums[i])){
				map.put(nums[i], map.get(nums[i])+1);
			}
			else{
				map.put(nums[i], 1);
			}
		}
		List<Integer> list=new ArrayList<Integer>(map.keySet());
		System.out.println(list.toString());
		
		Collections.sort(list, (o1, o2) -> (map.get(o2).compareTo(map.get(o1))));
		System.out.println(list.toString());
		
		int[] ans=new int[k];
		
		for(int i=0; i<k; i++){
			ans[i]=list.get(i);
		}

        return ans;
    }
	
}
~~~

-----
</br>
