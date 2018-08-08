	package offer;
	
	/**
	 * 题目描述 输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。 
	 * 如果是则输出Yes,否则输出No。假设输入的数组的任意两个数字都互不相同。
	 * 
	 * @author yanbowen
	 *
	 */
	public class A28_ErChaSuoYinShuDeHouXuBianLi {
		public boolean VerifySquenceOfBST(int[] sequence) {
			if (sequence.length == 0)
				return false;
			return VerifySquenceOfBST(sequence, 0, sequence.length - 1);
		}
	
		public boolean VerifySquenceOfBST(int[] sequence, int start, int end) {
			if (end <= start)
				return true;
			int i = start;
			for (; i < end; i++) {
				if (sequence[i] > sequence[end])
					break;
			}
			for (int j = i; j < end; j++) {
				if (sequence[j] < sequence[end])
					return false;
			}
			return VerifySquenceOfBST(sequence, start, i - 1) && VerifySquenceOfBST(sequence, i, end - 1);
		}
	
		public static void main(String[] args) {
			int arr[] = { 5, 7, 6, 9, 11, 10, 8 };
			A28_ErChaSuoYinShuDeHouXuBianLi bianLi = new A28_ErChaSuoYinShuDeHouXuBianLi();
			System.out.println(bianLi.VerifySquenceOfBST(arr));
		}
	}
