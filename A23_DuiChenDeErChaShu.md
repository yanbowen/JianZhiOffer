	package offer;
	
	/**
	 * 题目描述 请实现一个函数，用来判断一颗二叉树是不是对称的。 
	 * 注意，如果一个二叉树同此二叉树的镜像是同样的，定义其为对称的。
	 *
	 */
	public class A23_DuiChenDeErChaShu {
		public class TreeNode {
			int val = 0;
			TreeNode left = null;
			TreeNode right = null;
	
			public TreeNode(int val) {
				this.val = val;
			}
		}
	
		boolean isSymmetrical(TreeNode pRoot) {
			return isSymmetrical(pRoot, pRoot);
		}
	
		boolean isSymmetrical(TreeNode pRoot1, TreeNode pRoot2) {
			if (pRoot1 == null && pRoot2 == null) {
				return true;
			}
			if (pRoot1 == null || pRoot2 == null) {
				return false;
			}
	
			if (pRoot1.val != pRoot2.val) {
				return false;
			}
	
			return isSymmetrical(pRoot1.left, pRoot2.right) && isSymmetrical(pRoot1.right, pRoot2.left);
		}
	}
