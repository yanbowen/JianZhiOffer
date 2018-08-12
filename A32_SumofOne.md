	package offer;
	
	/**
	 * 题目描述
	 * 求出1~13的整数中1出现的次数,并算出100~1300的整数中1出现的次数？
	 * 为此他特别数了一下1~13中包含1的数字有1、10、11、12、13因此共出现6次,
	 * 但是对于后面问题他就没辙了。ACMer希望你们帮帮他,并把问题更加普遍化,
	 * 可以很快的求出任意非负整数区间中1出现的次数（从1到 n 中1出现的次数）。
	 * 
	 * https://www.cnblogs.com/xuanxufeng/p/6854105.html
	 */
	public class A32_SumofOne {
		public int NumberOf1Between1AndN_Solutions(int n) {
			int ones = 0;
			for (long m = 1; m <= n; m *= 10)
				ones += (n / m + 8) / 10 * m + (n / m % 10 == 1 ? n % m + 1 : 0);
			return ones;
		}
	
		public int NumberOf1Between1AndN_Solution(int n) {
			int sum = 0;
			for (int i = 1; i <= n; i++) {
				char[] array = String.valueOf(i).toCharArray();
				for (int j = 0; j < array.length; j++) {
					String s = String.valueOf(array[j]);
					if (s.equals("1")) {
						sum++;
					}
				}
			}
	
			return sum;
		}
	
		public static void main(String[] args) {
			A32_SumofOne a32_SumofOne = new A32_SumofOne();
			int i = a32_SumofOne.NumberOf1Between1AndN_Solution(1);
			System.out.println(i);
		}
	}
