	package offer;
	
	/*
	 * 题目 ：删除链表中重复的结点（122页）
	 * 
	 * 题目描述
	 * 		在一个排序的链表中，存在重复的结点，请删除该链表中重复的结点，重复的结点不保留，
	 * 		返回链表头指针。 例如，链表1->2->3->3->4->4->5 处理后为 1->2->5
	 * */
	public class A14_Deletes_repeated_nodes_in_a_linked_list {
	
		public static ListNode deleteDuplication(ListNode pHead) {
	
			if (pHead == null)
				return null;
			ListNode pH = pHead;
			ListNode pNode = new ListNode(0);
			ListNode pN = pNode;
			pNode.next = pHead;
			while (pH != null) {
				ListNode pHnext = pH.next;
				if (pHnext == null)
					break;
				if (pHnext.val == pH.val) {
					while (pHnext != null && pHnext.val == pH.val) {
						pHnext = pHnext.next;
					}
					pN.next = pHnext;
					pH = pHnext;
				} else {
					pN = pH;
					pH = pHnext;
				}
			}
			return pNode.next;
		}
	
		// 递归算法
		public ListNode deleteDuplication2(ListNode pHead) {
			if (pHead == null || pHead.next == null) { // 只有0个或1个结点，则返回
				return pHead;
			}
			if (pHead.val == pHead.next.val) { // 当前结点是重复结点
				ListNode pNode = pHead.next;
				while (pNode != null && pNode.val == pHead.val) {
					// 跳过值与当前结点相同的全部结点,找到第一个与当前结点不同的结点
					pNode = pNode.next;
				}
				return deleteDuplication(pNode); // 从第一个与当前结点不同的结点开始递归
			} else { // 当前结点不是重复结点
				pHead.next = deleteDuplication(pHead.next); // 保留当前结点，从下一个结点开始递归
				return pHead;
			}
		}
	
		public ListNode deleteDuplications(ListNode pHead) {
			// 删除链表中重复出现的结点(该程序实现的是将重复出现的值的结点保留一个
			if (pHead == null || pHead.next == null)
				return pHead;
			ListNode pre = pHead;
			ListNode late = pre.next;
			while (late != null) {
				if (pre.val == late.val) {
					pre.next = late.next;
					late = pre.next;
					continue;
				} else {
					pre = late;
					late = pre.next;
				}
			}
			return pHead;
		}
	
		public static class ListNode {
			int val;
			ListNode next = null;
	
			ListNode(int val) {
				this.val = val;
			}
		}
	
		public static void main(String[] args) {
			ListNode l1 = new ListNode(1);
			ListNode l2 = new ListNode(2);
			ListNode l3 = new ListNode(2);
			ListNode l4 = new ListNode(3);
			ListNode l5 = new ListNode(3);
			ListNode l6 = new ListNode(7);
			l1.next = l2;
			l2.next = l3;
			l3.next = l4;
			l4.next = l5;
			l5.next = l6;
			ListNode ln = deleteDuplication(l1);
			while (ln != null) {
				System.out.println(ln.val);
				ln = ln.next;
			}
		}
	}
