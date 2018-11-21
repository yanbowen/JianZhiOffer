	package offer;
	
	/*
	 * 题目 ：链表中环的入口结点（139页）
	 * 
	 * 题目描述:
	 * 		一个链表中包含环，请找出该链表的环的入口结点。
	 * 
	 * 思路:
	 * 		如果链表存在环，我们无需计算环的长度n，只需在相遇时，让一个指针在相遇点出发，
	 * 		另一个指针在链表首部出发，然后两个指针一次走一步，当它们相遇时，就是环的入口处。
	 */
	public class A18_The_entry_point_of_the_ring_in_the_list {
		public ListNode EntryNodeOfLoop(ListNode pHead) {
			if (pHead == null || pHead.next == null)
				return null;
	
			ListNode pFast = pHead;
			ListNode pSlow = pHead;
	
			while (pFast != null && pFast.next != null) {
				pSlow = pSlow.next;
				pFast = pFast.next.next;
				if (pSlow == pFast)
					break;
			}
			if (pFast != null) {
				pSlow = pHead;
				while (pSlow != pFast) {
					pSlow = pSlow.next;
					pFast = pFast.next;
				}
			}
	
			return pFast;
		}
	
		public class ListNode {
			int val;
			ListNode next = null;
	
			ListNode(int val) {
				this.val = val;
			}
		}
	}
