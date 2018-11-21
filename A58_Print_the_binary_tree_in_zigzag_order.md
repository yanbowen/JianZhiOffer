	package offer;
	
	/*
	 * 题目描述:
	 * 
	 * 请实现一个函数按照之字形打印二叉树，即第一行按照从左到右的顺序打印，
	 * 第二层按照从右至左的顺序打印，第三行按照从左到右的顺序打印，其他行以此类推。
	 */
	import java.util.ArrayDeque;
	import java.util.ArrayList;
	import java.util.Collections;
	import java.util.Queue;
	
	public class A58_Print_the_binary_tree_in_zigzag_order {
		public ArrayList<ArrayList<Integer>> Print(TreeNode pRoot) {
			ArrayList<ArrayList<Integer>> arraylist = new ArrayList<ArrayList<Integer>>();
			if (pRoot == null)
				return arraylist;
	
			Queue<TreeNode> queue = new ArrayDeque<TreeNode>();
			queue.add(pRoot);
			boolean flag = false;
	
			while (queue.size() != 0) {
				ArrayList<Integer> list = new ArrayList<Integer>();
				int len = queue.size();
				while (len > 0) {
					TreeNode t = queue.poll();
					len--;
					list.add(t.val);
					if (t.left != null)
						queue.add(t.left);
					if (t.right != null)
						queue.add(t.right);
				}
				if (flag) {
					Collections.reverse(list);
					flag = !flag;
				} else {
					flag = !flag;
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
