	package offer;
	
	/**
	 * 输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。
	 *
	 */
	public class A20_HeBinPaiXuLianBiao {
	
		public class Solution {
			public ListNode Merge(ListNode list1, ListNode list2) {
				ListNode result = null;
				ListNode resultNext = null;
	
				if (list1 == null) {
					return list2;
				}
				if (list2 == null) {
					return list1;
				}
	
				while (list1 != null && list2 != null) {
					if (list1.val <= list2.val) {
						if (result == null) {
							result = resultNext = list1;
						} else {
							resultNext.next = list1;
							resultNext = resultNext.next;
						}
						list1 = list1.next;
					} else {
						if (result == null) {
							result = resultNext = list2;
						} else {
							resultNext.next = list2;
							resultNext = resultNext.next;
						}
						list2 = list2.next;
					}
				}
	
				if (list1 == null) {
					resultNext.next = list2;
				} else {
					resultNext.next = list1;
				}
	
				return result;
			}
		}
	
		public class ListNode {
			int val;
			ListNode next = null;
	
			ListNode(int val) {
				this.val = val;
			}
		}
	}
