	package offer;
	
	import java.util.ArrayList;
	import java.util.Comparator;
	import java.util.PriorityQueue;
	
	/**
	 * 题目描述 输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。
	 * 
	 * @author yanbowen
	 *
	 */
	public class A40_ZuiXiao_K_num {
	
		// 构建大顶堆，每次只和堆顶比，如果比堆顶小，删除堆顶，新数入堆
		public ArrayList<Integer> GetLeastNumbers_Solution(int[] input, int k) {
			ArrayList<Integer> result = new ArrayList<Integer>();
			int length = input.length;
			if (k > length || k == 0) {
				return result;
			}
			PriorityQueue<Integer> maxHeap = new PriorityQueue<Integer>(k, new Comparator<Integer>() {
	
				@Override
				public int compare(Integer o1, Integer o2) {
					// 按value递减顺序排序
					return o2.compareTo(o1);
				}
			});
			for (int i = 0; i < length; i++) {
				if (maxHeap.size() != k) {
					maxHeap.offer(input[i]);
				} else if (maxHeap.peek() > input[i]) {
					Integer temp = maxHeap.poll();
					temp = null;
					maxHeap.offer(input[i]);
				}
			}
			for (Integer integer : maxHeap) {
				result.add(integer);
			}
			return result;
		}
	
		public static void main(String[] args) {
			int[] input = { 0, 2, 4, 8, 1, 6, 9, 11, 15, 17, 22 };
			int k = 4;
			A40_ZuiXiao_K_num obj = new A40_ZuiXiao_K_num();
			ArrayList<Integer> result = obj.GetLeastNumbers_Solution(input, k);
			System.out.println(result);
		}
	}
