	package offer;
	
	/*
	 * 题目 ：链表中倒数第k个结点（134页）
	 * 
	 * 题目描述
	 * 		输入一个链表，输出该链表中倒数第k个结点。
	 */
	public class A17_The_k_last_node_in_the_list {
		public class ListNode {
			int val;
			ListNode next = null;
	
			ListNode(int val) {
				this.val = val;
			}
		}
	
		public ListNode FindKthToTail(ListNode head, int k) {
	
			if (head == null || k <= 0)
				return null;
			ListNode flag = head;
			for (int i = 0; i < k - 1; i++) {
	
				if (flag.next != null) {
					flag = flag.next;
				} else {
					return null;
				}
			}
	
			while (flag.next != null) {
				flag = flag.next;
				head = head.next;
			}
			return head;
		}
	}
