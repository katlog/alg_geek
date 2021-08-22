## 泛型递归、树的递归
1. 泛型递归
   - 递归对应的模板
```c++
void recursion(Level level){
	// 终止条件
	if(){
		// 处理
		return;
	}
	
	// drill down

	recursion(level.nextLevel);

	// 状态恢复等
}
```
2. 树的递归
   - 树的遍历形式：前序、中序、后序、层序
   - 递归形式的前中后序比较简单，层序只有用队列的方式实现
```java
	   dfs(TreeNode node){
	   	if(node==null) return;
	   	// 根据顺序选择访问node
	   	dfs(node.left);
	   	dfs(node.right);
	   }
```
   - 遍历可以用栈、队列的方式进行

## 分治、回溯
1. 分治
   - 通常用递归的形式将问题进行分解，如。Pow(x,n)的问题
2. 回溯
   - 形式为递归，通过回溯某个步骤不断试错，找到问题答案。
```java
void backtracking(参数) {
    if (终止条件) {
        存放结果;
        return;
    }

    for (选择：本层集合中元素（树中节点孩子的数量就是集合的大小）) {
        处理节点;
        backtracking(路径，选择列表); // 递归
        回溯，撤销处理结果
    }
}
```
   - 这篇对回溯问题的总结非常赞：[回溯算法：重新安排行程](https://mp.weixin.qq.com/s/r73thpBnK1tXndFDtlsdCQ)