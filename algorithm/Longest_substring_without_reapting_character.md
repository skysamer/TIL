## ๐ก ์ค๋ณต ์๋ ๊ฐ์ฅ ๊ธด ๋ถ๋ถ ๋ฌธ์์ด
์ค๋ณต ๋ฌธ์๊ฐ ์๋ ๊ฐ์ฅ ๊ธด ๋ถ๋ถ ๋ฌธ์์ด์ ๊ธธ์ด๋ฅผ ๋ฆฌํดํ๋ ๋ฌธ์ ๋ค.

์ ๋ต์ ๋ฐ๋์ ๋ถ๋ถ ๋ฌธ์์ด์ด์ด์ผํ๋ค.

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
		
		int idx=0, len=0; //len์ ๋ฌธ์์ด์์ ์ฐพ์์ ์๋ ์ต๋ ๋น์ค๋ณต ๋ฌธ์์ด ๊ธธ์ด๋ฅผ ์ ์ฅํ๋ ๋ณ์
		
		/*๋ฐ๋ณต๋ฌธ์ผ๋ก map์ ๋ฌธ์์ด์ ํ ์์ฉ ์ฝ์ํ๋ฉด์ ๊ฒ์ฆํ๋ค.*/
		for(int i=0; i<s.length(); i++){
			char c=s.charAt(i);
			
			/*์ค๋ถ key๊ฐ ๋ค์ด์์ ๊ฒฝ์ฐ*/
			if(map.containsKey(c) && idx<=map.get(c)){
				idx=map.get(c)+1; // ์ค๋ณต key๊ฐ ๋ค์ด์๋ value+1๋ก idx๊ฐ์ ๋ณ๊ฒฝ
			}
			map.put(c, i);
			
			/**idx์ ๋ณํ๊ฐ ์์ผ๋ฉด len์ 1์ฉ ์ฆ๊ฐํจ
			 * idx์ ๋ณํ๊ฐ ์๋ค = ์ค๋ณต๋ฌธ์๊ฐ ๋ค์ด์ค์ง ์์๋ค.
			 * idx์ ๋ณํ๊ฐ ์๊ธธ ๊ฒฝ์ฐ len๊ฐ์ด ๋ณํ์ง ์๋๋ค.*/
			len=Math.max(len, i-idx+1);
		}
		
        return len;
    }
	
}

~~~

-----
</br>
