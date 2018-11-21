	package offer;
	
	/*
	 * 题目 ：数组中出现次数超过一半的数字（205页）
	 * 
	 * 题目描述 :
	 * 
	 * 数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。
	 * 例如输入一个长度为9的数组{1,2,3,2,2,2,5,4,2}。由于数字2在数组中出现了5次， 
	 * 超过数组长度的一半， 因此输出2。如果不存在则输出0。
	 *
	 * 题解：
	 * 当遍历到下一个数字的时候，如果下一个数字和我们之前保存的数字相同，则次数加1；
	 * 否则次数减1；如果次数为零，我们需要保存下一个数，并把次数设置为1.
	 * 由于，我们找的数字比其他数字之和还要多，那么要找出数字肯定是最后一个次数为1时的对应数字。
	 */
	public class A39_A_number_that_occurs_more_than_half_the_time_in_an_array {
	
		public int MoreThanHalfNum_Solution(int[] array) {
			int n = array.length;
			if (n == 0) {
				return 0;
			}
			int count = 1;
			int num = array[0];
			for (int i = 1; i < n; i++) {
				if (count == 0) {
					num = array[i];
					count = 1;
					continue;
				}
				if (num == array[i]) {
					count = count + 1;
				} else {
					count = count - 1;
				}
			}
			// Verifying
			count = 0;
			for (int i = 0; i < n; i++) {
				if (array[i] == num)
					count++;
			}
			if (count * 2 > n)
				return num;
			return 0;
		}
	}
