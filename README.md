## Binary Search Trees

### Objectives

- Learn what makes a tree a binary search tree
- Learn how to find and insert elements into a binary search tree
- Learn about the benefits of finding elements via a binary search tree vs arrays and linked lists.

### Binary Search Trees

Let's now discuss a specific type of tree: binary search trees.  Binary search trees are trees where we organize the nodes such that the nodes adhere to two rules:

  1. No parent can have more than two children (thus binary)
  2. Each left child node is less than it's parent node, and each right child is more than the parent node.

Let's try inserting the numbers one through six, in an increasing sequence: 1, 2, 3, 4, 5, 6.

```text
T1 T2  T3     T4       T5           T6

1  1    1     1         1            1
    2    2     2         2            2
          3     3         3            3
                 4         4            4
                            5            5
                                          6
```

The diagram above illustrates the following.  We are indicating every separate time that we insert a new node on top, with T1 as the first step, T2 as the second, and so on (T stands for time).  The root node is the first node that we begin with, the number 1.  In T2, because 2 is larger than 1, we place it to the right.  Then we take the number 3.  Three is larger than 1, so we place it on the branch to the right, but a 2 is already there.  So then we ask is 3 larger than 2, it is.  So we place 3 on the branch to the right of the 2.  Because each succeeding number is larger than all of the previous numbers, we continue to place each number one branch to the right of the previously inserted number.

Note that our trees look very different if we insert them in a different order.  For example, let's place the numbers in a binary search tree but this time in the following order:  4, 1, 2, 5, 6, 3.

```text
   T1       T2     T3       T4             T5            T6

   4        4      4         4             4              4
           /      /        /   \         /   \          /   \
          1      1        1     5       1     5        1     5
                   \       \             \     \        \     \
                   2        2            2     6        2     6
                                                         \
                                                          3
```

The diagram above illustrates the steps involved in inserting each node into a binary search tree.  Here, the root node is the first node that we begin with, the number 4.  Then in T2, because 1 is less than 4, we place the number to the left.  In T3, we take the number 2.  Two is less than four, so it belongs to the left of four.  Because 1 is already to the left of four, we need to place the 2 one more level down.  Now 2 is greater than 1, so we place it to the right of the node with the number 1.  So if you look at our tree at T3, you can see that the number 2 is to the left of all of the numbers that it is smaller than, the number four.  And it is to the right of all of the numbers that it is larger than, the number 1.  Trace the subsequent steps followed at T4, T5 and T6.  

Also note that the each of the trees above hold data in one direction: each parent node knows about it's children, but the children do not know information about their parent.  This is called a **directed tree**.  It may make more sense when we translate the tree into code in the next section.

> A directed tree is a tree where each parent node holds a pointer to its children, but children do not know about their parent.  

### Representing Binary Search Trees in Javascript

So far we know that binary search trees consist of nodes, with each node having a maximum of two children.  So it sounds like each node stores three pieces of information: it's own data, it's right child node, and the left child node.

```javascript

  let node = {data: 4, rightChild: null, leftChild: null}
```

Let's represent the following numbers: 6, 1, 4, 8 in a binary search tree.

```javascript
  let bst = {data: 6, 
  				rightChild: {data: 8, leftChild: null, rightChild: null},
      		  	leftChild: {data: 1,
          		rightChild: {data: 4, rightChild: null, leftChild: null},
			leftChild: null}
              }}
```
If we deconstruct the above tree, we see that the root node is the first object, which has a pointer to a leftChild of a node with data 1.  That left child has a pointer to a right child with data 4.  So a diagram of our tree would look like:

```text
  T1   T2      T3

  6     6      6
       /      / \
      1      1   8
              \
               4
```

### Summary 

In this section we learned how to structure a binary search tree.  With a binary search tree, each child node to the left should be less than its parent node, and each child node to the right should be more than its parent node.  We saw that we can represent a binary search tree in Javascript through the use of objects.  In the next section, we'll explore some of the benefits of structuring our data as a binary search tree, as well as how to perform functions like adding elements to our tree.

<p class='util--hide'>View <a href='https://learn.co/lessons/binary-search-trees'>Binary Search Trees</a> on Learn.co and start learning to code for free.</p>
