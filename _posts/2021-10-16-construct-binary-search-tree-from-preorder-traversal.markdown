---
layout: post
title:  "Construct Binary Search Tree from Preorder Traversal"
date:   2021-10-16 10:38:29 +0300
categories: algorithms
---
Given an array of integers preorder, which represents the **preorder traversal** of a BST (i.e., **binary search tree**), construct the tree and return its root.

It is **guaranteed** that there is always possible to find a binary search tree with the given requirements for the given test cases.

A **binary search** tree is a binary tree where for every node, any descendant of `Node.left` has a value strictly less than `Node.val`, and any descendant of `Node.right` has a value strictly greater than `Node.val`.

A preorder traversal of a binary tree displays the value of the node first, then traverses `Node.left`, then traverses `Node.right`.

{% highlight ruby %}
# Definition for a binary tree node.
class TreeNode
    attr_accessor :val, :left, :right
    def initialize(val = 0, left = nil, right = nil)
        @val = val
        @left = left
        @right = right
    end
end

# @param {Integer[]} preorder
# @return {TreeNode}
def bst_from_preorder(preorder)
  i = 0
  root = TreeNode.new preorder[i]

  while i < preorder.size - 1 do
    i = i + 1
    traverse(root, preorder[i])
  end
  
  root
end

def traverse(node, val)
  if node.val > val
    if node.left.nil?
      node.left = TreeNode.new val
    else
      traverse(node.left, val)
    end
  else
    if node.right.nil?
      node.right = TreeNode.new val
    else
      traverse(node.right, val)
    end
  end
end
{% endhighlight %}
