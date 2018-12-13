	package offer;
	
	/*
	 * 题目描述：
	 * 
	 * 从上到下按层打印二叉树，同一层结点从左至右输出。每一层输出一行。
	 */
	import java.util.*;
	
	public class A_01_the_level_of_binary_tree_traversal {
		// last ：表示正在打印的当前行的最右节点
		// nlast ：表示下一行的最右节点
		public int[][] printTrees(TreeNode root) {
			ArrayList<ArrayList<Integer>> res = new ArrayList<ArrayList<Integer>>();
			ArrayList<Integer> temp = new ArrayList<Integer>();
			LinkedList<TreeNode> queue = new LinkedList<TreeNode>();
			queue.offer(root);
			TreeNode node = null;
			TreeNode last = root;
			TreeNode nlast = last;
			if (root == null)
				return null;
			while (!queue.isEmpty()) {
				node = queue.poll();
				temp.add(node.val);
				if (node.left != null) {
					queue.offer(node.left);
					nlast = node.left;
				}
				if (node.right != null) {
					queue.offer(node.right);
					nlast = node.right;
				}
				if (node == last) {
					res.add(temp);
					temp = new ArrayList<Integer>();
					last = nlast;
				}
			}
			int[][] result = new int[res.size()][];
			for (int i = 0; i < res.size(); i++) {
				result[i] = new int[res.get(i).size()];
				for (int j = 0; j < result[i].length; j++) {
					result[i][j] = res.get(i).get(j);
				}
			}
			return result;
		}
	
		public int[][] printTree(TreeNode root) {
			ArrayList<ArrayList<Integer>> res = new ArrayList<ArrayList<Integer>>();
			if (root == null) {
				return null;
			}
			Queue<TreeNode> queue = new LinkedList<TreeNode>();
			queue.offer(root);
			while (queue.size() != 0) {
				ArrayList<Integer> list = new ArrayList<Integer>();
				int length = queue.size();
				while (length > 0) {
					TreeNode node = queue.poll();
					length--;
					list.add(node.val);
					if (node.left != null) {
						queue.offer(node.left);
					}
					if (node.right != null) {
						queue.offer(node.right);
					}
				}
				res.add(list);
			}
			int[][] result = new int[res.size()][];
			for (int i = 0; i < res.size(); i++) {
				result[i] = new int[res.get(i).size()];
				for (int j = 0; j < result[i].length; j++) {
					result[i][j] = res.get(i).get(j);
				}
			}
			return result;
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
