	package offer;
	
	/* 
	 * 题目 ：从尾到头打印链表（P58）
	 * 
	 * 输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。
	 * */
	import java.util.ArrayList;
	import java.util.Stack;
	
	public class A02_Print_list_from_end_to_start {
		public class ListNode {
			int val;
			ListNode next = null;
	
			ListNode(int val) {
				this.val = val;
			}
		}
	
		/**
		 * 递归方式
		 */
		ArrayList<Integer> arrayList = new ArrayList<Integer>();
	
		public ArrayList<Integer> printListFromTailToHeads(ListNode listNode) {
	
			if (listNode != null) {
				this.printListFromTailToHead(listNode.next);
				arrayList.add(listNode.val);
			}
			return arrayList;
		}
	
		/**
		 * 栈存储方式
		 * 
		 * @param listNode
		 * @return 链表
		 */
	
		public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
	
			Stack<Integer> stack = new Stack<Integer>();
			ArrayList<Integer> arrayList = new ArrayList<Integer>();
	
			while (listNode != null) {
				stack.push(listNode.val);
				listNode = listNode.next;
			}
	
			while (!stack.isEmpty()) {
				arrayList.add(stack.pop());
			}
	
			return arrayList;
		}
	}
