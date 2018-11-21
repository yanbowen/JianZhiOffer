	package offer;
	
	public class A52_AVL_Tree {
		public boolean IsBalanced_Solution(TreeNode root) {
			int left = TreeDepth(root.left);
			int right = TreeDepth(root.right);
			return Math.abs(left - right) > 1 ? false : true;
		}
	
		private int TreeDepth(TreeNode pRoot) {
			if (pRoot == null) {
				return 0;
			}
			int left = TreeDepth(pRoot.left);
			int right = TreeDepth(pRoot.right);
			return left > right ? (left + 1) : (right + 1);
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
