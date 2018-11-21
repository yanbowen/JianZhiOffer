	package offer;
	
	/*
	 * 题目 ：数字在排序数组中出现的次数（275页）
	 * 
	 * 题目描述:
	 * 
	 * 统计一个数字在排序数组中出现的次数。例如，输入排序数组{1,2,3,3,3,3,4,5}和数字3，
	 * 输出 3
	 * 
	 */
	public class A36_The_number_of_occurrences_of_a_number_in_a_sorted_array {
		public int GetNumberOfK(int[] array, int k) {
			int length = array.length;
			if (length == 0) {
				return 0;
			}
			int firstK = getFirstK(array, k, 0, length - 1);
			int lastK = getLastK(array, k, 0, length - 1);
			if (firstK != -1 && lastK != -1) {
				return lastK - firstK + 1;
			}
			return 0;
		}
	
		// 递归写法 (二分查找)
		private int getFirstK(int[] array, int k, int start, int end) {
			if (start > end) {
				return -1;
			}
			int mid = (start + end) >> 1;
			if (array[mid] > k) {
				return getFirstK(array, k, start, mid - 1);
			} else if (array[mid] < k) {
				return getFirstK(array, k, mid + 1, end);
			} else if (mid - 1 >= 0 && array[mid - 1] == k) {
				return getFirstK(array, k, start, mid - 1);
			} else {
				return mid;
			}
		}
	
		// 循环写法 (二分查找)
		private int getLastK(int[] array, int k, int start, int end) {
			int length = array.length;
			int mid = (start + end) >> 1;
			while (start <= end) {
				if (array[mid] > k) {
					end = mid - 1;
				} else if (array[mid] < k) {
					start = mid + 1;
				} else if (mid + 1 < length && array[mid + 1] == k) {
					start = mid + 1;
				} else {
					return mid;
				}
				mid = (start + end) >> 1;
			}
			return -1;
		}
	
		public static void main(String[] args) {
			int[] arr = { 1, 2, 3, 3, 3, 3, 4, 5 };
			int k = 3;
			A36_The_number_of_occurrences_of_a_number_in_a_sorted_array array = new A36_The_number_of_occurrences_of_a_number_in_a_sorted_array();
			int i = array.GetNumberOfK(arr, k);
			System.out.println(i);
		}
	}
