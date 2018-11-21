	package offer;
	
	import java.util.Arrays;
	
	/*
	 * 题目描述
	 * 
	 * 一个整型数组里除了两个数字之外，其他的数字都出现了偶数次。请写程序找出这两个只出现一次的数字。
	 */
	public class A50_appears_only_once_in_array {
		public void FindNumsAppearOnce(int[] array, int num1[], int num2[]) {
			Arrays.sort(array);
			boolean flag = true;
			for (int i = 0; i < array.length; i = i + 2) {
				if (i + 1 < array.length - 1 && array[i] != array[i + 1]) {
					if (i - 1 < 0 || array[i - 1] != array[i]) {
						if (flag) {
							num1[0] = array[i];
							flag = false;
							i--;
						} else {
							num2[0] = array[i];
							break;
						}
					}
	
				} else {
					if (!flag) {
						num2[0] = array[i];
					} else {
						num1[0] = array[i];
						num2[0] = array[i + 1];
					}
	
				}
			}
		}
	}
