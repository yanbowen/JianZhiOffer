	package offer;
	
	/*
	 * 题目 ：圆圈中最后剩下的数（300页）
	 * 
	 * 题目描述:
	 * 
	 * 0,1,2,...,n-1 这n个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数字。
	 * 求出这个圆圈里剩下的最后一个数字。
	 */
	public class A44_The_last_number_left_in_the_circle {
		public int LastRemaining_Solution(int n, int m) {
			// 约瑟夫环
			if (n < 1 || m < 1) {
				return -1;
			}
			int last = 0;
			for (int i = 2; i <= n; i++) {
				last = (last + m) % i;
			}
			return last;
		}
	}
