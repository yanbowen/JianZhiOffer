	package offer;
	
	/*
	 * 题目描述:
	 * 
	 * 给定一个数组A[0,1,...,n-1],请构建一个数组B[0,1,...,n-1],
	 * 其中B中的元素B[i]=A[0]*A[1]*...*A[i-1]*A[i+1]*...*A[n-1]。不能使用除法。
	 */
	public class A57_Constructing_Product_Arrays {
		public int[] multiply(int[] A) {
			if (A == null || A.length == 0)
				return null;
			int length = A.length;
			int[] arr1 = new int[length];
			int[] arr2 = new int[length];
			arr1[0] = 1;
			arr2[length - 1] = 1;
			for (int i = 1; i < length; i++) {
				arr1[i] = A[i - 1] * arr1[i - 1];
				arr2[length - 1 - i] = A[length - i] * arr2[length - i];
			}
			for (int i = 0; i < length; i++) {
				arr1[i] = arr1[i] * arr2[i];
			}
			return arr1;
	
		}
	}
