	package offer;
	
	/*
	 * 题目 ：和为S的两个数字（280页）
	 * 
	 * 题目描述:
	 * 
	 * 输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。
	 * {1,2,4,7,11,15} 由于4+11=15，输出4,11
	 */
	import java.util.ArrayList;
	
	public class A37_two_Numbers_for_S {
		public ArrayList<Integer> FindNumbersWithSum(int[] array, int sum) {
			// 既然是排序好的，就使用：左右加逼
			ArrayList<Integer> list = new ArrayList<Integer>();
			if (array == null || array.length < 2) {
				return list;
			}
			int i = 0, j = array.length - 1;
			while (i < j) {
				if (array[i] + array[j] == sum) {
					list.add(array[i]);
					list.add(array[j]);
					return list;
				} else if (array[i] + array[j] > sum) {
					j--;
				} else {
					i++;
				}
	
			}
			return list;
		}
	
		public ArrayList<Integer> FindNumbersWithSums(int[] array, int sum) {
			int result = Integer.MAX_VALUE;
			int num = 0;
			ArrayList<Integer> list = new ArrayList<>();
			if (array == null) {
				return list;
			}
			for (int i = 0; i < array.length; i++) {
				num = array[i];
				for (int j = i + 1; j < array.length; j++) {
					if (array[j] == sum - num) {
						if (result > num * array[j]) {
							if (list.size() != 0) {
								list.clear();
							}
							result = num * array[j];
							list.add(num);
							list.add(array[j]);
						}
						break;
					}
				}
			}
			return list;
		}
	}
