	package offer;
	
	/*
	 * 题目 ：把字符串转换成整数
	 * 
	 * 题目描述：
	 * 
	 * 将一个字符串转换成一个整数(实现Integer.valueOf(string)的功能，
	 * 但是string不符合数字要求时返回0)，要求不能使用字符串转换整数的库函数。 
	 * 数值为0或者字符串不是一个合法的数值则返回0。
	 * 
	 * 输入
	 * +2147483647
	 * 1a33
	 * 
	 * 输出
	 * 2147483647
	 * 0
	 */
	import java.math.BigInteger;
	
	public class A47_Convert_the_string_to_an_integer {
		public int StrToInt(String str) {
			if (str == null || str.length() == 0) {
				return 0;
			}
			int flag = 1;
			BigInteger bi;
			if (str.charAt(0) + "" == "+") {
				str = str.substring(1, str.length());
			} else if (str.charAt(0) + "" == "-") {
				flag = flag * -1;
			}
	
			try {
				bi = new BigInteger(str);
	
			} catch (Exception e) {
				return 0;
			}
			return bi.intValue() * flag;
		}
	
		public int StrToInts(String str) {
			if (str == null || str.length() == 0)
				return 0;
			char[] a = str.toCharArray();
			int fuhao = 0;
			if (a[0] == '-')
				fuhao = 1;
			int sum = 0;
			for (int i = fuhao; i < a.length; i++) {
				if (a[i] == '+')
					continue;
				if (a[i] < 48 || a[i] > 57)
					return 0;
				sum = sum * 10 + a[i] - 48;
			}
			return fuhao == 0 ? sum : sum * -1;
		}
	}
