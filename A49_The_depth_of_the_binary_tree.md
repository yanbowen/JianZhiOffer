	package offer;
	
	/*
	 * 题目描述
	 * 输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）
	 * 形成树的一条路径，最长路径的长度为树的深度。
	 */
	import java.util.LinkedList;
	import java.util.Queue;
	
	public class A49_The_depth_of_the_binary_tree {
	
		/**
		 * 非递归写法：层次遍历
		 * 
		 * @param pRoot
		 * @return
		 */
		public int TreeDepth(TreeNode pRoot) {
			if (pRoot == null) {
				return 0;
			}
			Queue<TreeNode> queue = new LinkedList<TreeNode>();
			queue.add(pRoot);
			int depth = 0, count = 0, nextCount = 1;
			while (queue.size() != 0) {
				TreeNode top = queue.poll();
				count++;
				if (top.left != null) {
					queue.add(top.left);
				}
				if (top.right != null) {
					queue.add(top.right);
				}
				if (count == nextCount) {
					nextCount = queue.size();
					count = 0;
					depth++;
				}
			}
			return depth;
		}
	
		/**
		 * 递归写法
		 * 
		 * @param pRoot
		 * @return
		 */
		public int TreeDepths(TreeNode pRoot) {
			if (pRoot == null) {
				return 0;
			}
			int left = TreeDepths(pRoot.left);
			int right = TreeDepths(pRoot.right);
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
