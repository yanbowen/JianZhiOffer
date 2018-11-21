	package offer;
	
	/*
	 * 题目 ：变态跳台阶（P78）
	 * 
	 * 题目描述
	 * 		一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。
	 * 		求该青蛙跳上一个n级的台阶总共有多少种跳法。
	 * */
	public class A11_Abnormal_Jump_steps {
		public int JumpFloorII(int target) {
			if (target < 0)
				return 0;
			if (target == 1)
				return 1;
			if (target == 2)
				return 2;
	
			int arr[] = new int[target + 1];
			arr[1] = 1;
			arr[2] = 2;
	
			for (int i = 3; i <= target; i++) {
				int sum = 0;
				for (int j = 1; j < i; j++) {
					sum += arr[j];
				}
				arr[i] = sum + 1;
			}
	
			return arr[target];
		}
	
		public static void main(String[] args) {
			A11_Abnormal_Jump_steps hua = new A11_Abnormal_Jump_steps();
	
			System.out.println(hua.JumpFloorII(8));
		}
	}
