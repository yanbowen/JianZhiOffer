	package offer;
	
	/* 
	 * 题目 ：二维数组中的查找（P44）
	 * 
	 * 在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。
	 * 请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
	 * */
	public class A01_Lookup_in_two_dimensional_arrays {
		public boolean Find(int target, int[][] array) {
	
			boolean result = false;
			int rows = array.length;
			int columns = array[0].length - 1;
			int row = 0;
	
			while (row < rows && columns >= 0) {
				int value = array[row][columns];
				if (target > value) {
					row++;
				} else if (target < value) {
					columns--;
				} else {
					result = true;
					break;
				}
			}
			return result;
		}
	
		public String replaceSpace(StringBuffer str) {
			// String s = str.toString().replace(" ", "%20");
			// return s;
	
			StringBuffer buffer = new StringBuffer();
			for (int i = 0; i < str.length(); i++) {
				if (str.charAt(i) == ' ') {
					buffer.append("%20");
				} else {
					buffer.append(str.charAt(i));
				}
			}
			return buffer.toString();
		}
	}
