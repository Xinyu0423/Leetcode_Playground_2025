# Tree Methodology(Tree相关方法论)

## 四种遍历方法
- 前序遍历
  - 根-左-右
- 中序遍历
  - 左-根-右
- 后序遍历
  - 左-右-根
- 层序遍历
  - 逐层遍历
  
## 递归的思维模式
- 递归三要素
  - 终止条件(Base case)
    - 需要保证递归函数的返回值是相同的(不能一部分返回True/False，一部分返回None)
  - 处理当前节点
  - 递归子问题(ex:递归左子树，递归右子树)

## 树的题目类别
- 遍历类：
  - 前中后序，层序遍历，齿距遍历
- 路径类：
  - 直径，路径和，最长路径
- 子树类：
  - 相同树，子树判断，重复子树
- 构建类：
  - 从遍历序列构建（前序遍历+中序遍历，前序遍历+后序遍历，中序遍历+后序遍历）
  - 从描述构建树（通过序列化）
- 属性类：
  - 深度，宽度，平衡性，完全性
- 关系类
  - 找到祖先（上一层），找到兄弟（同一层），找到堂兄弟（同一层但不是相同祖先）
- 操作类
  - 合并树，序列化树，插入节点，删除节点

## 辅助数据结构
- 需要记录父节点关系：Hashmap({节点: 父节点})
- 需要快速查找节点值的位置：Hashmap({节点: index})
- 需要序列化比较: Hashmap({序列化字符串: 出现的次数})
- 需要维护层次信息：队列+深度信息 (ex:queue.append([node, level]))或者 队列 + visited信息(ex:queue.append([node, visited]))

## 从上到下的递归（前序思维）
```Python
def dfs(root):
    str = ""
    if root is None:
        return ""
    str += str(root.val) + ','
    str += dfs(root.left)
    str += dfs(root.right)
    return str
```
- 需要从上到下传递信息
- 处理每个节点时，需要得到祖先节点的信息
- 不需要从子节点获取信息来计算当前节点
- Leetcode: 1448, 662

## 从下到上的递归（后序思维）
```Python
def dfs(root):
    str = ""
    if root is None:
        return ""
    str += dfs(root.left)
    str += dfs(root.right)
    str += str(root.val) + ','
    return str
```
- 当前节点依赖于左右子树的答案
- 需要从叶子节点开始计算
- 通常需要返回某些信息给父节点
- Leetcode: 543, 563, 104

## Return类型
- 找节点 → return 节点
- 判真假 → return bool
- 算高度 → return 数
  - return max(left, right)？
    - 你要返回一个沿树往上累积的数值（如高度、深度、路径长度）
      - 高度/深度Leetcode: 104, 111
      - 最长路径Leetcode: 543, 124
    - 左右子树各自能给你一个“数值”（不能是bool 或节点）
- 要路径 → return list
- 只遍历 → return None