	package offer;
	
	/*
	 * 题目 ：旋转数组的最小数字（P82）
	 * 
	 * 题目描述
	 * 		把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。 输入一个非递减排序的数组的一个旋转，
	 * 		输出旋转数组的最小元素。 例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为1。 
	 * 		NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。
	 * */
	public class A08_Rotates_the_minimum_number_of_an_array {
	
		public int minNumberInRotateArray(int[] array) {
	
			if (array.length == 0) {
				return 0;
			}
			int start = 0;
			int end = array.length - 1;
			int middle = 0;
			while (array[start]>=array[end]) {
				if ((start + 1) == end) {
					break;
				}
				middle = (start + end) / 2;
				if (array[start] <= array[middle]) {
					start = middle;
				}
				if (array[end] >= array[middle]) {
					end = middle;
				}
	
			}
			return array[end];
		}
	}
