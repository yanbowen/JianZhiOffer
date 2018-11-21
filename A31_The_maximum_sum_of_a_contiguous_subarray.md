	package offer;
	
	/*
	 * 题目 ：连续子数组的最大和（218页）
	 * 
	 * 题目描述:
	 * 
	 * 输入一个整型数组，数组里有正数也有负数。数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。
	 */
	import java.util.ArrayList;
	import java.util.Collections;
	import java.util.List;
	
	public class A31_The_maximum_sum_of_a_contiguous_subarray {
	
		int FindGreatestSumOfSubArrays(int[] array) {
			if (array.length == 0)
				return 0;
			int sum = array[0], tempsum = array[0]; // 注意初始值 不能设为0 防止只有负数
			for (int i = 1; i < array.length; i++) // 从1开始 因为0的情况在初始化时完成了
			{
				tempsum = (tempsum < 0) ? array[i] : tempsum + array[i];
				sum = (tempsum > sum) ? tempsum : sum;
			}
			return sum;
		}
	
		public int FindGreatestSumOfSubArray(int[] array) {
			int sum = array[0];
			int sumTemp = 0;
			if (array.length == 0 || array == null) {
				return sum;
			}
			List<Integer> list = new ArrayList<>();
			for (int i = 0; i < array.length; i++) {
				int temp = sumTemp + array[i];
				if (temp > 0) {
					sumTemp = sumTemp + array[i];
					list.add(sumTemp);
				}
				if (temp < 0) {
					if (list.size() == 0) {
						if (sum < temp) {
							sum = temp;
						}
					} else {
						sum = (sum > Collections.max(list)) ? sum : Collections.max(list);
						list.clear();
						sumTemp = 0;
					}
	
				}
				if (i == array.length - 1 || sumTemp > sum) {
					if (list.size() == 0) {
						if (sum < temp) {
							sum = temp;
						}
					} else {
						sum = (sum > Collections.max(list)) ? sum : Collections.max(list);
					}
				}
			}
			return sum;
		}
	
		public static void main(String[] args) {
			int[] arr = { 1, -2, 3, 10, -4, 7, 2, -5 };
			// int[] arr = { 1, -2, 3, 10, 4, 7, -2, -5 };
			// int[] arr = { -2, -8, -1, -5, -9 };
			A31_The_maximum_sum_of_a_contiguous_subarray array = new A31_The_maximum_sum_of_a_contiguous_subarray();
			int i = array.FindGreatestSumOfSubArrays(arr);
			System.out.println(i);
		}
	}
