	package offer;
	
	/*
	 * 题目 ：求1+2+3+...+n（307页）
	 * 
	 * 题目描述：
	 * 
	 * 求1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。
	 */
	public class A45_Solution {
		public int Sum_Solution(int n) {
			int result = n;
			boolean flag = (n > 0) && ((result += Sum_Solution(n - 1)) > 0);
			return result;
		}
	}