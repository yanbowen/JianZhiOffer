	package offer;
	
	/*
	 * 题目 ：翻转单词顺序列（284页）
	 * 
	 * 题目描述:
	 * 
	 * 输入一个英文单词，翻转句子中单词的顺序，但单词内字符的顺序不变。
	 * 例：输入"I am a student."
	 * 输出 "student. a am I"
	 */
	public class A41_Flip_the_word_order_column {
		public String ReverseSentence(String str) {
			if (str == null) {
				return null;
			}
			// trim() 方法用于删除字符串的头尾空白符
			if (str.trim().equals("")) {
				return str;
			}
			StringBuilder builder = new StringBuilder();
			String[] strs = str.split(" ");
			for (int i = strs.length - 1; i >= 0; i--) {
				builder.append(strs[i]);
				if (i >= 1) {
					builder.append(" ");
				}
			}
			return builder.toString();
		}
	}
