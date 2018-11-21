	package offer;
	
	/*
	 * 题目描述：
	 * 
	 * 从上到下按层打印二叉树，同一层结点从左至右输出。每一层输出一行。
	 */
	import java.util.*;
	
	public class A59_the_level_of_binary_tree_traversal {
		ArrayList<ArrayList<Integer>> Print(TreeNode pRoot) {
			ArrayList<ArrayList<Integer>> arraylist = new ArrayList<ArrayList<Integer>>();
			if (pRoot == null) {
				return arraylist;
			}
			Queue<TreeNode> queue = new ArrayDeque<TreeNode>();
			queue.add(pRoot);
			while (queue.size() != 0) {
				ArrayList<Integer> list = new ArrayList<Integer>();
				int length = queue.size();
				while (length > 0) {
					TreeNode node = queue.poll();
					length--;
					list.add(node.val);
					if (node.left != null) {
						queue.add(node.left);
					}
					if (node.right != null) {
						queue.add(node.right);
					}
				}
				arraylist.add(list);
			}
			return arraylist;
	
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
