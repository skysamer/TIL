## 💡 전화번호 문자 조합
2에서 9까지 숫자가 주어졌을때 전화번호로 조합 가능한 모든 문자를 출력하는 문제다.

주어진 숫자의 개수만큼 문자열의 길이를 설정하고 그에 맞는 문자열만 출력해야 한다.

Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
Example 2:

Input: digits = ""
Output: []

Example 3:

Input: digits = "2"
Output: ["a","b","c"]

재귀호출을 활용한 DFS로 구현했다.

~~~java
public class Solution {
	/**
	 * 배열 순서가 핸드폰의 각 번호로 매핑됨
	 * 번호에 매핑된 문자들의 조합
	 * */
	public static String[] dic={"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
	public static List<String> result;
	
	public static List<String> letterCombinations(String digits) {
		result=new ArrayList<>();
		
		if(digits.length()==0){
			return new ArrayList<>();
		}
		
		/**
		 * digits을 배열화하여 첫 번째 인덱스에 해당하는 값을 가져온다.
		 * */
		combination(0, new StringBuilder(), digits.toCharArray());
		
        return result;
    }
	
	public static void combination(int pick, StringBuilder sb, char[] digitArr){
		/**
		 * 즉, sb의 길이가 digits의 길이와 같을때만 배열에 insert 시킨다.
		 * 이후 해당 재귀를 빠져나옴*/
		if(pick==digitArr.length){
			result.add(sb.toString());
			return;
		}
		
		/*digits 배열의 첫번째 인덱스에 해당하는 값을 인덱스로 하는 dic의 값을 가져온다.*/
		char[] dicArr=dic[Character.getNumericValue(digitArr[pick])].toCharArray();
		
		/**
		 * pick > digitArr.length인 경우
		 * 마지막 재귀를 빠져나온 후
		 * delete() 메서드를 수행하여 마지막단에 붙어있는  문자를 제거하고
		 * 다시 반복문을 순회하면서 나머지 조합을 맞춰 result 배별에 삽입한다.
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
