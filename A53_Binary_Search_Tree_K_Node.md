	package offer;
	
	/*
	 * 题目描述:
	 * 
	 * 给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8） 中，按结点数值大小顺序第三小结点的值为4。
	 */
	public class A53_Binary_Search_Tree_K_Node {
		// 思路：二叉搜索树按照中序遍历的顺序打印出来正好就是排序好的顺序。
		// 所以，按照中序遍历顺序找到第k个结点就是结果。
		public class Solution {
			int index = 0; // 计数器
	
			TreeNode KthNode(TreeNode root, int k) {
				if (root != null) { // 中序遍历寻找第k个
					TreeNode node = KthNode(root.left, k);
					if (node != null)
						return node;
					index++;
					if (index == k)
						return root;
					node = KthNode(root.right, k);
					if (node != null)
						return node;
				}
				return null;
			}
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
