	package offer;
	
	/*
	 * 题目描述：
	 * 
	 * 给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）
	 * 中，按结点数值大小顺序第三小结点的值为4。
	 */
	import java.util.*;
	
	public class A60_Binary_search_tree_k_node {
		TreeNode KthNode(TreeNode pRoot, int k) {
			if (pRoot == null) {
				return null;
			}
			ArrayList<TreeNode> list = new ArrayList<TreeNode>();
			Queue<TreeNode> queue = new ArrayDeque<TreeNode>();
			queue.add(pRoot);
			while (queue.size() != 0) {
				int length = queue.size();
				while (length > 0) {
					TreeNode node = queue.poll();
					list.add(node);
					length--;
					if (node.left != null) {
						queue.add(node.left);
					}
					if (node.right != null) {
						queue.add(node.right);
					}
				}
			}
	
			Collections.sort(list, new Comparator<TreeNode>() {
	
				@Override
				public int compare(TreeNode o1, TreeNode o2) {
					if (o2.val - o1.val < 0) {
						return 1;
					} else {
						return -1;
					}
				}
			});
	
			return list.get(k - 1);
	
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
