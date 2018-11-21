	package offer;
	
	/*
	 * 题目 ：第一个只出现一次的字符（243页）
	 * 
	 * 题目描述:
	 * 
	 * 在一个字符串(0<=字符串长度<=10000，全部由字母组成)中找到第一个只出现一次的字符,
	 * 并返回它的位置, 如果没有则返回 -1（需要区分大小写）.
	 */
	import java.util.ArrayList;
	
	public class A35_The_first_character_that_appears_only_once {
		public int FirstNotRepeatingChar(String str) {
			int result = -1;
			if (str == null || str.length() == 0) {
				return result;
			}
			ArrayList<Character> list1 = new ArrayList<Character>();
			ArrayList<Character> list2 = new ArrayList<Character>();
			for (int i = 0; i < str.length(); i++) {
				if (!list2.contains(str.charAt(i))) {
					list1.add(str.charAt(i));
					list2.add(str.charAt(i));
				} else {
					list1.remove(Character.valueOf(str.charAt(i)));
				}
	
			}
			if (list1.get(0) != null) {
				result = str.indexOf(String.valueOf(list1.get(0)));
			}
			return result;
		}
	
		public static void main(String[] args) {
			String str = "google";
			A35_The_first_character_that_appears_only_once once = new A35_The_first_character_that_appears_only_once();
			int i = once.FirstNotRepeatingChar(str);
			System.out.println(i);
		}
	}
