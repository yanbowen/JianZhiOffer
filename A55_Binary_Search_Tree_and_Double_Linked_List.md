	package offer;
	
	/*
	 * 题目描述:
	 * 
	 * 输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的双向链表。要求不能创建任何新的结点，只能调整树中结点指针的指向。
	 * 中序排序
	 */
	public class A55_Binary_Search_Tree_and_Double_Linked_List {
	
		TreeNode head = null;
		TreeNode realHead = null;
	
		public TreeNode Convert(TreeNode pRootOfTree) {
			ConvertSub(pRootOfTree);
			return realHead;
		}
	
		private void ConvertSub(TreeNode pRootOfTree) {
			if (pRootOfTree == null)
				return;
			ConvertSub(pRootOfTree.left);
			if (head == null) {
				head = pRootOfTree;
				realHead = pRootOfTree;
			} else {
				head.right = pRootOfTree;
				pRootOfTree.left = head;
				head = pRootOfTree;
			}
			ConvertSub(pRootOfTree.right);
		}
	
		public class TreeNode {
			int val = 0;
			TreeNode left = null;
			TreeNode right = null;
	
			public TreeNode(int val) {
				this.val = val;
			}
		}
	}
