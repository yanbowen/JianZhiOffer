	package offer;
	
	/*
	 * 题目 ：二叉搜索树的后序遍历序列（182页）
	 * 
	 * 题目描述:
	 * 
	 * 输入一颗二叉树的跟节点和一个整数，打印出二叉树中结点值的和为输入整数的所有路径。
	 * 路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。
	 * (注意: 在返回值的list中，数组长度大的数组靠前)
	 */
	import java.util.ArrayList;
	
	public class A29_A_path_that_is_balanced_by_a_value_in_a_binary_tree {
		private ArrayList<ArrayList<Integer>> listAll = new ArrayList<ArrayList<Integer>>();
		private ArrayList<Integer> list = new ArrayList<Integer>();
	
		public ArrayList<ArrayList<Integer>> FindPath(TreeNode root, int target) {
			if (root == null)
				return listAll;
			list.add(root.val);
			target -= root.val;
			if (target == 0 && root.left == null && root.right == null)
				listAll.add(new ArrayList<Integer>(list));
			FindPath(root.left, target);
			FindPath(root.right, target);
			list.remove(list.size() - 1);
			return listAll;
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
