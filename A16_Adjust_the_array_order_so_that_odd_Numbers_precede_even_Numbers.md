	package offer;
	
	import java.util.Arrays;
	
	/*
	 * 题目 ：调整数组顺序使奇数位于偶数前面（129页）
	 * 
	 * 题目描述
	 * 
	 * 输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，
	 * 所有的偶数位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。
	 */
	public class A16_Adjust_the_array_order_so_that_odd_Numbers_precede_even_Numbers {
	
		public void reOrderArray(int[] array) {
			for (int i = 0; i < array.length - 1; i++) {
				for (int j = 0; j < array.length - i - 1; j++) {
					if (array[j] % 2 == 0 && array[j + 1] % 2 != 0) {
						array[j] = array[j] ^ array[j + 1];
						array[j + 1] = array[j] ^ array[j + 1];
						array[j] = array[j] ^ array[j + 1];
					}
				}
			}
		}
	
		/**
		 * 实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，
		 * 所有的偶数位于位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。
		 * 
		 * @param array
		 */
		public void reOrderArray1(int[] array) {
			if (array == null || array.length == 0)
				return;
			int start = 0;
			int arrs[] = new int[array.length];
			for (int i = 0; i < array.length; i++) {
				if (fun(array[i])) {
					arrs[start] = array[i];
					start++;
				}
			}
			for (int i = 0; i < array.length; i++) {
				if (funs(array[i])) {
					arrs[start] = array[i];
					start++;
				}
			}
			array = arrs;
		}
	
		boolean fun(int arr) {
			if (arr % 2 != 0)
				return true;
			else
				return false;
		}
	
		boolean funs(int arr) {
			if (arr % 2 == 0)
				return true;
			else
				return false;
		}
	
		/**
		 * 使得所有的奇数位于数组的前半部分，所有的偶数位于位于数组的后半部分
		 * 
		 * @param array
		 */
		public void reOrderArray2(int[] array) {
			if (array == null || array.length == 0)
				return;
			int start = 0;
			int end = array.length - 1;
			while (start < end) {
				while (array[start] % 2 != 0) {
					start++;
				}
				while (array[end] % 2 == 0) {
					end--;
				}
				if (start < end) {
					array[start] = array[start] + array[end];
					array[end] = array[start] - array[end];
					array[start] = array[start] - array[end];
				}
			}
		}
	
		public static void main(String[] args) {
			int[] array = { 2, 2, 1, 3, 2, 2, 1 };
			System.out.println(Arrays.toString(array));
			A16_Adjust_the_array_order_so_that_odd_Numbers_precede_even_Numbers xu = new A16_Adjust_the_array_order_so_that_odd_Numbers_precede_even_Numbers();
			xu.reOrderArray(array);
			System.out.println(Arrays.toString(array));
		}
	}
