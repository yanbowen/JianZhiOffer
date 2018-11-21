	package offer;
	
	/*
	 * 题目 ：两个链表的第一个公共结点（P253）
	 * 
	 * 题目描述:
	 * 
	 * 输入两个链表，找出它们的第一个公共结点。
	 * 思路：找出长的链表，先走过多出来的距离，然后两表都是遍历
	 */
	public class A51_The_first_common_node_of_two_lists {
	
		/**
		 * 不计长度，短链表每次相当于追赶上长链表比锻炼表长出的距离。
		 * 
		 * @param pHead1
		 * @param pHead2
		 * @return
		 */
		public ListNode FindFirstCommonNodes(ListNode pHead1, ListNode pHead2) {
			ListNode p1 = pHead1;
			ListNode p2 = pHead2;
			while (p1 != p2) {
				p1 = (p1 == null ? pHead2 : p1.next);
				p2 = (p2 == null ? pHead1 : p2.next);
			}
			return p1;
		}
	
		public ListNode FindFirstCommonNode(ListNode pHead1, ListNode pHead2) {
			int pList1 = getLength(pHead1);
			int pList2 = getLength(pHead2);
			int pListDif = pList1 - pList2;
	
			ListNode longList = pHead1;
			ListNode shortList = pHead2;
			if (pList1 < pList2) {
				pListDif *= -1;
				longList = pHead2;
				shortList = pHead1;
			}
	
			for (int i = 0; i < pListDif; i++) {
				longList = longList.next;
			}
			while (longList != shortList) {
				longList = longList.next;
				shortList = shortList.next;
			}
			return longList;
		}
	
		/**
		 * 
		 * @param pHead
		 * @return 返回链表长度
		 */
		private int getLength(ListNode pHead) {
			int temp = 0;
			ListNode head = pHead;
			while (true) {
				if (head != null) {
					temp++;
					head = head.next;
				} else {
					break;
				}
			}
			return temp;
		}
	
		public class ListNode {
			int val;
			ListNode next = null;
	
			ListNode(int val) {
				this.val = val;
			}
		}
	}
