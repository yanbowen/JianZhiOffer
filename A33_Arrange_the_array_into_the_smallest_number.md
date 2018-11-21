	package offer;
	
	/*
	 * 题目 ：把数组排成最小的数（227页）
	 * 
	 * 题目描述:
	 * 
	 * 输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。
	 * 例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为321323。
	 */
	import java.util.ArrayList;
	import java.util.Collections;
	import java.util.Comparator;
	
	public class A33_Arrange_the_array_into_the_smallest_number {
	
		public String PrintMinNumber(int[] numbers) {
	
			String result = "";
			ArrayList<Integer> list = new ArrayList<Integer>();
			for (int i = 0; i < numbers.length; i++) {
				list.add(numbers[i]);
			}
	
			Collections.sort(list, new Comparator<Integer>() {
	
				@Override
				public int compare(Integer o1, Integer o2) {
	
					String s1 = o1 + "" + o2;
					String s2 = o2 + "" + o1;
	
					return s1.compareTo(s2);
				}
			});
	
			for (Integer integer : list) {
				result += integer;
			}
			return result;
	
		}
	}
