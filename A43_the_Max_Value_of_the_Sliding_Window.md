	package offer;
	
	/*
	 * 题目 ：滑动窗口的最大值
	 * 
	 * 题目描述:
	 * 
	 * 给定一个数组和滑动窗口的大小，找出所有滑动窗口里数值的最大值。
	 * 例如，如果输入数组{2,3,4,2,6,2,5,1}及滑动窗口的大小3，那么一共存在6个滑动窗口，
	 * 他们的最大值分别为{4,4,6,6,6,5}； 针对数组{2,3,4,2,6,2,5,1}的滑动窗口有以下6个：
	 *  {[2,3,4],2,6,2,5,1}， {2,[3,4,2],6,2,5,1}， {2,3,[4,2,6],2,5,1}， 
	 *  {2,3,4,[2,6,2],5,1}， {2,3,4,2,[6,2,5],1}， {2,3,4,2,6,[2,5,1]}。
	 */
	import java.util.*;
	
	public class A43_the_Max_Value_of_the_Sliding_Window {
		public ArrayList<Integer> maxInWindows(int[] num, int size) {
			ArrayList<Integer> list = new ArrayList<Integer>();
			if (num == null || num.length == 0 || size <= 0 || num.length < size) {
				return list;
			}
			if (num.length == size) {
				Arrays.sort(num);
				list.add(num[num.length - 1]);
				return list;
			}
			int result = Integer.MIN_VALUE;
	
			for (int j = 0; j < num.length; j++) {
				if (j + size > num.length) {
					break;
				}
				for (int i = 0; i < size; i++) {
					if (num[i + j] > result) {
						result = num[i + j];
					}
				}
				list.add(result);
				result = Integer.MIN_VALUE;
			}
			return list;
		}
	}
