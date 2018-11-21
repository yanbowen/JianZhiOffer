	package offer;
	
	/*
	 * 题目 ：左旋转字符串
	 * 
	 * 题目描述:
	 * 
	 * 字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。
	 * 例如，字符序列S=”abcXYZdef”,要求输出循环左移3位后的结果，即“XYZdefabc”。
	 */
	public class A42_Left_hand_rotation_string {
		public String LeftRotateString(String str, int n) {
			if (str == null) {
				return null;
			}
			if (n <= 0 || str.length() == 0) {
				return str;
			}
			StringBuilder builder = new StringBuilder();
			for (int i = n; i < str.length(); i++) {
				builder.append(str.charAt(i));
			}
			for (int i = 0; i < n; i++) {
				builder.append(str.charAt(i));
			}
			return builder.toString();
		}
	}
