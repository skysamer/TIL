## ๐ก ์ ํ๋ฒํธ ๋ฌธ์ ์กฐํฉ
2์์ 9๊น์ง ์ซ์๊ฐ ์ฃผ์ด์ก์๋ ์ ํ๋ฒํธ๋ก ์กฐํฉ ๊ฐ๋ฅํ ๋ชจ๋  ๋ฌธ์๋ฅผ ์ถ๋ ฅํ๋ ๋ฌธ์ ๋ค.

์ฃผ์ด์ง ์ซ์์ ๊ฐ์๋งํผ ๋ฌธ์์ด์ ๊ธธ์ด๋ฅผ ์ค์ ํ๊ณ  ๊ทธ์ ๋ง๋ ๋ฌธ์์ด๋ง ์ถ๋ ฅํด์ผ ํ๋ค.

Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
Example 2:

Input: digits = ""
Output: []

Example 3:

Input: digits = "2"
Output: ["a","b","c"]

์ฌ๊ทํธ์ถ์ ํ์ฉํ DFS๋ก ๊ตฌํํ๋ค.

~~~java
public class Solution {
	/**
	 * ๋ฐฐ์ด ์์๊ฐ ํธ๋ํฐ์ ๊ฐ ๋ฒํธ๋ก ๋งคํ๋จ
	 * ๋ฒํธ์ ๋งคํ๋ ๋ฌธ์๋ค์ ์กฐํฉ
	 * */
	public static String[] dic={"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
	public static List<String> result;
	
	public static List<String> letterCombinations(String digits) {
		result=new ArrayList<>();
		
		if(digits.length()==0){
			return new ArrayList<>();
		}
		
		/**
		 * digits์ ๋ฐฐ์ดํํ์ฌ ์ฒซ ๋ฒ์งธ ์ธ๋ฑ์ค์ ํด๋นํ๋ ๊ฐ์ ๊ฐ์ ธ์จ๋ค.
		 * */
		combination(0, new StringBuilder(), digits.toCharArray());
		
        return result;
    }
	
	public static void combination(int pick, StringBuilder sb, char[] digitArr){
		/**
		 * ์ฆ, sb์ ๊ธธ์ด๊ฐ digits์ ๊ธธ์ด์ ๊ฐ์๋๋ง ๋ฐฐ์ด์ insert ์ํจ๋ค.
		 * ์ดํ ํด๋น ์ฌ๊ท๋ฅผ ๋น ์ ธ๋์ด*/
		if(pick==digitArr.length){
			result.add(sb.toString());
			return;
		}
		
		/*digits ๋ฐฐ์ด์ ์ฒซ๋ฒ์งธ ์ธ๋ฑ์ค์ ํด๋นํ๋ ๊ฐ์ ์ธ๋ฑ์ค๋ก ํ๋ dic์ ๊ฐ์ ๊ฐ์ ธ์จ๋ค.*/
		char[] dicArr=dic[Character.getNumericValue(digitArr[pick])].toCharArray();
		
		/**
		 * pick > digitArr.length์ธ ๊ฒฝ์ฐ
		 * ๋ง์ง๋ง ์ฌ๊ท๋ฅผ ๋น ์ ธ๋์จ ํ
		 * delete() ๋ฉ์๋๋ฅผ ์ํํ์ฌ ๋ง์ง๋ง๋จ์ ๋ถ์ด์๋  ๋ฌธ์๋ฅผ ์ ๊ฑฐํ๊ณ 
		 * ๋ค์ ๋ฐ๋ณต๋ฌธ์ ์ํํ๋ฉด์ ๋๋จธ์ง ์กฐํฉ์ ๋ง์ถฐ result ๋ฐฐ๋ณ์ ์ฝ์ํ๋ค.
		 * */
		for(int i=0; i<dicArr.length; i++){
			sb.append(dicArr[i]);
			combination(pick+1, sb, digitArr);
			sb.delete(sb.length()-1, sb.length());
		}
	}
	
}

~~~

-----
</br>
