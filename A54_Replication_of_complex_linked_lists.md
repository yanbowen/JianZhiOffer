	package offer;
	
	/*
	 * 题目描述:
	 * 
	 * 输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，
	 * 另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的head。
	 */
	public class A54_Replication_of_complex_linked_lists {
		public RandomListNode Clone(RandomListNode pHead) {
			if (pHead == null) {
				return pHead;
			}
			RandomListNode head = pHead;
			// 复制next 如原来是A->B->C 变成A->A'->B->B'->C->C'
			while (head != null) {
				RandomListNode node = new RandomListNode(head.label);
				node.next = head.next;
				head.next = node;
				head = node.next;
			}
	
			head = pHead;
			// 复制random pCur是原来链表的结点 pCur.next是复制pCur的结点
			while (head != null) {
				if (head.random != null)
					head.next.random = head.random.next;
				head = head.next.next;
			}
	
			RandomListNode second = pHead.next;
			RandomListNode mark = second;
			head = pHead;
			// 拆分链表
			while (head != null) {
				head.next = head.next.next;
				if (mark.next != null)
					mark.next = mark.next.next;
				head = head.next;
				mark = mark.next;
			}
			return second;
	
		}
	
		public class RandomListNode {
			int label;
			RandomListNode next = null;
			RandomListNode random = null;
	
			RandomListNode(int label) {
				this.label = label;
			}
		}
	}
