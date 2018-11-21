	package offer;
	
	/*
	 * 题目 ：数组中重复的数字（P39）
	 * 
	 * 题目描述
	 *		在一个长度为n的数组里的所有数字都在0到n-1的范围内。 数组中某些数字是重复的，但不知道有几个数字是重复的。
	 *		也不知道每个数字重复几次。请找出数组中任意一个重复的数字。 例如，如果输入长度为7的数组{2,3,1,0,2,5,3}，
	 *		那么对应的输出是第一个重复的数字2。
	 * 
	 * Parameters:
	 *	numbers:     an array of integers
	 *	length:      the length of array numbers
	 *	duplication: (Output) the duplicated number in the array number,length of duplication array is 1,so using duplication[0] = ? in implementation; Here duplication like pointor in C/C++, duplication[0] equal *duplication in C/C++
	 *		这里要特别注意~返回任意重复的一个，赋值duplication[0]
	 *	Return value:       true if the input is valid, and there are some duplications in the array number
		otherwise false
	 */
	import java.util.HashMap;
	import java.util.Map;
	
	public class A05_A_repeated_number_in_an_array {
	
		public boolean duplicate(int numbers[], int length, int[] duplication) {
	
			if (numbers == null) {
				return false;
			}
	
			HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
			for (int i = 0; i < numbers.length; i++) {
	
				if (map.containsKey(Integer.valueOf(numbers[i]))) {
					map.put(Integer.valueOf(numbers[i]), map.get(Integer.valueOf(numbers[i])) + 1);
				} else {
					map.put(Integer.valueOf(numbers[i]), 1);
				}
			}
	
			for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
				if (entry.getValue() != 1) {
					duplication[0] = entry.getKey();
					return true;
				}
			}
			return false;
		}
	
		public boolean duplicates(int numbers[], int length, int[] duplication) {
			StringBuffer sb = new StringBuffer();
			for (int i = 0; i < length; i++) {
				sb.append(numbers[i] + "");
			}
			for (int j = 0; j < length; j++) {
				if (sb.indexOf(numbers[j] + "") != sb.lastIndexOf(numbers[j] + "")) {
					duplication[0] = numbers[j];
					return true;
				}
			}
			return false;
		}
	}
