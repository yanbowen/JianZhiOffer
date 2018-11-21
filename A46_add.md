	package offer;
	
	import java.math.BigInteger;
	
	/*
	 * 题目 ：不用加减乘除做加法（P310）
	 * 
	 * 题目描述
	 * 
	 * 写一个函数，求两个整数之和，要求在函数体内不得使用+、-、*、/四则运算符号。
	 */
	public class A46_add {
		public int Add(int num1, int num2) {
			int sum, carry;
			do {
				sum = num1 ^ num2;
				carry = (num1 & num2) << 1;
				num1 = sum;
				num2 = carry;
			} while (num2 != 0);
			return num1;
		}
	
		public int Adds(int num1, int num2) {
			BigInteger bi1 = new BigInteger(String.valueOf(num1));
			BigInteger bi2 = new BigInteger(String.valueOf(num2));
			return bi1.add(bi2).intValue();
		}
	}
