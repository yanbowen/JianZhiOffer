	package offer;
	
	/*
	 * 题目描述
	 * 		一个链表中包含环，请找出该链表的环的入口结点。
	 */
	public class A18_LianBiaoZhongHuan {
		public ListNode EntryNodeOfLoop(ListNode pHead) {
			if (pHead == null || pHead.next == null)
				return null;
	
			ListNode first = MeetingNode(pHead);
			if (first == null)
				return null;
			int count = 0;
			ListNode Ncount = first;
			while (first != Ncount.next) {
				count++;
				Ncount = Ncount.next;
			}
	
			ListNode pre = pHead;
			ListNode end = pHead;
	
			for (int i = 0; i <= count; i++) {
				pre = pre.next;
			}
	
			while (pre != end) {
				pre = pre.next;
				end = end.next;
			}
			return pre;
		}
	
		public ListNode MeetingNode(ListNode pHead) {
			if (pHead == null) {
				return null;
			}
	
			ListNode second = pHead.next;
			ListNode first = second.next;
	
			while (first != null && second != null) {
				if (first == second) {
					return first;
				}
				first = first.next;
				second = second.next;
	
				if (first != null)
					first = first.next;
			}
	
			return null;
	
		}
	
		public class ListNode {
			int val;
			ListNode next = null;
	
			ListNode(int val) {
				this.val = val;
			}
		}
	}
