	package offer;
	
	/**
	 * 题目描述
	 * 从上往下打印出二叉树的每个节点，同层节点从左至右打印。
	 */
	import java.util.ArrayList;
	
	public class A27_DaYinErChaShu {
		public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {
			ArrayList<Integer> arrayList = new ArrayList<Integer>();
			if (root == null)
				return arrayList;
			arrayList.add(root.val);
			PrintFromTopToBottom(arrayList, root);
			return arrayList;
		}
	
		public void PrintFromTopToBottom(ArrayList<Integer> arrayList, TreeNode root) {
	
			if (root.left != null)
				arrayList.add(root.left.val);
			if (root.right != null)
				arrayList.add(root.right.val);
			if (root.left != null) {
				TreeNode roots = root.left;
				PrintFromTopToBottom(arrayList, roots);
			}
	
			if (root.right != null) {
				TreeNode roots = root.right;
				PrintFromTopToBottom(arrayList, roots);
			}
		}
	
		public static void main(String[] args) {
			TreeNode node = new TreeNode(10);
			node.left = new TreeNode(6);
			node.right = new TreeNode(14);
	
			TreeNode node1 = node.left;
			node1.left = new TreeNode(4);
			node1.right = new TreeNode(8);
	
			TreeNode node2 = node.right;
			node2.left = new TreeNode(12);
			node2.right = new TreeNode(16);
	
			A27_DaYinErChaShu shu = new A27_DaYinErChaShu();
			shu.PrintFromTopToBottom(node);
		}
	
		public static class TreeNode {
			int val = 0;
			TreeNode left = null;
			TreeNode right = null;
	
			public TreeNode(int val) {
				this.val = val;
	
			}
	
		}
	}
