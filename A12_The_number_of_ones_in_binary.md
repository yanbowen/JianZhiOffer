	package offer;
	
	/*
	 * 题目 ：二进制中1的个数（P100）
	 * 
	 * 题目描述
	 * 		输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。
	 * */
	public class A12_The_number_of_ones_in_binary {
		public int NumberOf1(int n) {
	
			int flag = 1, count = 0;
			while (flag != 0) {
				if ((flag & n) != 0)
					count++;
				flag = flag << 1;
			}
			return count;
		}
	
		public int NumberOf1s(int n) {
			int t = 0;
			char[] ch = Integer.toBinaryString(n).toCharArray();
			for (int i = 0; i < ch.length; i++) {
				if (ch[i] == '1') {
					t++;
				}
			}
			return t;
		}
	
		public int NumberOfOne(int n) {
			int count = 0;
			while (n != 0) {
				count++;
				n = (n - 1) & n;
			}
			return count;
		}
	}
