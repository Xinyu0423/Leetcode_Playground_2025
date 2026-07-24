# Stack方法论

## Stack(栈)的应用场景及通用技巧
- 栈主要应用于处理匹配对，路径，序列验证的问题
  -  括号匹配：遇到左括号入栈，右括号检查栈顶是否匹配
  -  路径简化：用栈来检查当前的有效路径（ex：Leetcode 71）
  -  相邻元素处理：栈顶元素与当前元素满足某些条件时的处理（ex：Leetcode 1544，1209）
  -  序列验证：模拟栈操作，验证序列的合法性（ex：Leetcode 946，1441）

## 如何识别栈的问题
- 需要处理嵌套结构：括号，HTML标签
- 撤销操作或者经常需要回到上一步：浏览历史，Text Editor
- 维护当前的最大/最小值：Monotonic Stack
- 寻找每个元素的左右边界：Monotonic Stack
- 涉及相关元素的比较：每日温度
- 找Rectangle的Area（ex：leetcode 1504， 84）：Monotonic Stack
- 模拟数学计算(Leetcode 224, 227)

## 单调栈(Monotonic Stack)
- 核心思想：
  - 单调栈内的每个元素都在等待其“终结者”
- 递增栈（找更小元素）：
  - 当前元素小于栈顶元素，栈顶元素的终结者出现
  - 计算栈顶元素的结果，弹出，之后继续比较
  - 当前元素入栈，等待它的终结者
- 递减栈（找更大元素）：
  - 当前元素大于栈顶元素，栈顶元素的终结者出现
  - 计算栈顶元素的结果，弹出，之后继续比较
  - 当前元素入栈，等待它的终结者
- 模版
```Python
stack = []
result = 初始化结果
for i, current in enumerate(arr):
    while stack and 满足pop条件(stack[-1]大于或者小于current):
        popped_element = stack.pop()
        result = 更新结果
    if 决策是否push元素:
        stack.append(处理当前元素index or value/current)
收尾处理，清理栈中剩余元素
while stack:
    popped_element = stack.pop()
    result = 处理剩余元素(popped_element)
return result
```

## 处理嵌套结构
- 处理括号
  - 模版
  ```Python
  stack = []
  for char in s:
    if char是左括号:
        入栈
    if char是右括号，检查与栈顶是否匹配:
        如果匹配，出栈栈顶元素（匹配到一组括号）
        如果不匹配，说明存在非法括号
  最后检查栈是否为空
  ```

## 双Stack设计
- 用于同时维护多种信息
- 应用：最小栈，浏览器历史，Text editor