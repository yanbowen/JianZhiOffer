	package offer;
	
	/*
	 * 题目 ：和为S的连续正数序列（282页）
	 * 
	 * 题目描述:
	 * 
	 * 输入一个正数sum,输出所有和为sum的连续正数序列（至少含有两个数）。
	 * 例如，输入15，由于，1+2+3+4+5=4+5+6=7+8=15
	 */
	import java.util.ArrayList;
	
	public class A38_The_sum_is_a_continuous_positive_sequence_of_S {
		public ArrayList<ArrayList<Integer>> FindContinuousSequence(int sum) {
			ArrayList<ArrayList<Integer>> arrayList = new ArrayList<ArrayList<Integer>>();
			int small = 1;
			int big = 2;
			int middle = (1 + sum) / 2;
			int result = small + big;
			while (small < middle) {
				if (result == sum) {
					ArrayList<Integer> list = new ArrayList<Integer>();
					for (int i = small; i <= big; i++) {
						list.add(i);
					}
					arrayList.add(list);
				}
				while (result > sum && small < middle) {
					result -= small;
					small++;
					if (result == sum) {
						ArrayList<Integer> list = new ArrayList<Integer>();
						for (int i = small; i <= big; i++) {
							list.add(i);
						}
						arrayList.add(list);
					}
				}
				big++;
				result += big;
			}
			return arrayList;
		}
	
		public static void main(String[] args) {
			int sum = 9;
			A38_The_sum_is_a_continuous_positive_sequence_of_S s = new A38_The_sum_is_a_continuous_positive_sequence_of_S();
			ArrayList<ArrayList<Integer>> list = s.FindContinuousSequence(sum);
			System.out.println(list.toString());
		}
	}
