## 💡 중복 없는 가장 긴 부분 문자열
중복 문자가 없는 가장 긴 부분 문자열의 길이를 리턴하는 문제다.

정답은 반드시 부분 문자열이어야한다.

Example 1:

Input: s = "abcabcbb"
Output: 3

Example 2:

Input: s = "bbbbb"
Output: 1

Example 3:

Input: s = "pwwkew"
Output: 3

~~~java
public class StringSolution {
	
	public static int lengthOfLongestSubstring(String s) {
		HashMap<Character, Integer> map=new HashMap<>();
		
		int idx=0, len=0; //len은 문자열에서 찾을수 있는 최대 비중복 문자열 길이를 저장하는 변수
		
		/*반복문으로 map에 문자열의 한 자씩 삽입하면서 검증한다.*/
		for(int i=0; i<s.length(); i++){
			char c=s.charAt(i);
			
			/*중북 key가 들어왔을 경우*/
			if(map.containsKey(c) && idx<=map.get(c)){
				idx=map.get(c)+1; // 중복 key가 들어있는 value+1로 idx값을 변경
			}
			map.put(c, i);
			
			/**idx에 변화가 없으면 len은 1씩 증가함
			 * idx에 변화가 없다 = 중복문자가 들어오지 않았다.
			 * idx에 변화가 생길 경우 len값이 변하지 않는다.*/
			len=Math.max(len, i-idx+1);
		}
		
        return len;
    }
	
}

~~~

-----
</br>
