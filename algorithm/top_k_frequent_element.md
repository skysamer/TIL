## ๐ก ์์ K ๋น๋ ์์
๋ฐฐ์ด์ ๋ฑ์ฅํ๋ ๋น๋์๋ฅผ ๊ธฐ์ค์ผ๋ก ์์ k๊ฐ ์์ ๋ค์ด์ค๋ ์์๋ค์ ๋ฆฌํดํ๋ ๋ฌธ์ ๋ค.

ํด์๋งต ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ  key์ ์์๋ฅผ ๋ฃ๊ณ  value์ ๊ฐ ์์์ ๊ฐ์๋ฅผ ์ ์ฅํ๋ค.
list ๊ฐ์ฒด๋ฅผ ์์ฑํ๊ณ , value๋ฅผ ๊ธฐ์ค์ผ๋ก key๋ฅผ ์ ๋ ฌํ ๋ค์ list์ ์์ฐจ์ ์ผ๋ก ์ฝ์ํ๋ค.

ํฌ๊ธฐ๊ฐ ์์ k๊ฐ์ธ ๋ฐฐ์ด์ ์์ฑํ๊ณ  list์ ๊ฐ์ ์์ k๊ฐ ๋งํผ ๋ฐฐ์ด์ ์ฝ์ํ๊ณ  ๋ฐฐ์ด์ ๋ฆฌํดํ๋ค.

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
