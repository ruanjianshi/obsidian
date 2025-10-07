# 哈希

## 哈希表基础
哈希表是一种通过哈希函数将键映射到值的数据结构，具有O(1)的平均时间复杂度用于插入、删除和查找。哈希冲突通过链地址法或开放地址法解决。

**核心概念**：
- 哈希函数：将键转换为数组索引
- 冲突处理：多个键映射到同一位置时的解决方案
- 负载因子：元素数量与哈希表容量的比值

**常见应用**：
- 两数之和
- 字符串中的第一个唯一字符
- 同构字符串

## 示例代码
```cpp
// 两数之和 - 使用哈希表存储已遍历元素
vector<int> twoSum(vector<int>& nums, int target) {
    // 哈希表：key为数值，value为索引
    unordered_map<int, int> hashTable;
    
    for (int i = 0; i < nums.size(); i++) {
        int complement = target - nums[i];
        // 检查补数是否已存在于哈希表中
        if (hashTable.count(complement)) {
            // 返回补数的索引和当前索引
            return {hashTable[complement], i};
        }
        // 将当前元素及其索引存入哈希表
        hashTable[nums[i]] = i;
    }
    return {};
}
```

## 刷题记录

---

# 双指针

## 双指针技巧
双指针使用两个指针在数组或链表中移动，通常用于解决以下问题：
- 查找满足特定条件的元素对
- 反转数组或链表
- 合并有序数组

**常见模式**：
- 快慢指针：检测环、找中点
- 左右指针：二分查找、三数之和
- 同向指针：滑动窗口、删除重复项

## 示例代码
```cpp
// 反转链表 - 双指针法
ListNode* reverseList(ListNode* head) {
    ListNode* prev = nullptr;  // 前驱节点
    ListNode* curr = head;     // 当前节点
    
    while (curr != nullptr) {
        // 保存下一个节点
        ListNode* nextTemp = curr->next;
        // 反转指针方向
        curr->next = prev;
        // 前进指针
        prev = curr;
        curr = nextTemp;
    }
    
    return prev;  // 新的头节点
}

// 三数之和 - 排序+双指针
vector<vector<int>> threeSum(vector<int>& nums) {
    vector<vector<int>> result;
    sort(nums.begin(), nums.end());  // 排序
    
    for (int i = 0; i < nums.size() - 2; i++) {
        // 跳过重复元素
        if (i > 0 && nums[i] == nums[i - 1]) continue;
        
        int left = i + 1;           // 左指针
        int right = nums.size() - 1; // 右指针
        int target = -nums[i];      // 目标和
        
        while (left < right) {
            int sum = nums[left] + nums[right];
            
            if (sum == target) {
                result.push_back({nums[i], nums[left], nums[right]});
                // 跳过重复元素
                while (left < right && nums[left] == nums[left + 1]) left++;
                while (left < right && nums[right] == nums[right - 1]) right--;
                left++;
                right--;
            } else if (sum < target) {
                left++;  // 和太小，左指针右移
            } else {
                right--; // 和太大，右指针左移
            }
        }
    }
    return result;
}
```

## 刷题记录

---

# 滑动窗口

## 滑动窗口算法
滑动窗口是一种在数组或字符串中寻找满足特定条件的子数组/子串的算法。维护一个可变大小的窗口，通过移动窗口来寻找最优解。

**关键步骤**：
1. 初始化窗口边界
2. 扩展窗口直到条件满足
3. 收缩窗口以寻找更优解
4. 保存最优结果

**常见应用**：
- 最小覆盖子串
- 无重复字符的最长子串
- 滑动窗口最大值

## 示例代码
```cpp
// 无重复字符的最长子串
int lengthOfLongestSubstring(string s) {
    // 哈希表存储字符及其最新出现的位置
    unordered_map<char, int> charIndex;
    int maxLength = 0;
    int left = 0;  // 窗口左边界
    
    for (int right = 0; right < s.size(); right++) {
        char c = s[right];
        // 如果字符已存在于窗口中，移动左边界
        if (charIndex.count(c) && charIndex[c] >= left) {
            left = charIndex[c] + 1;
        }
        // 更新字符位置
        charIndex[c] = right;
        // 更新最大长度
        maxLength = max(maxLength, right - left + 1);
    }
    return maxLength;
}

// 最小覆盖子串
string minWindow(string s, string t) {
    unordered_map<char, int> need, window;
    // 统计t中每个字符的出现次数
    for (char c : t) need[c]++;
    
    int left = 0, right = 0;
    int valid = 0;  // 窗口中满足条件的字符数
    int start = 0, len = INT_MAX;
    
    while (right < s.size()) {
        char c = s[right];
        right++;  // 扩大窗口
        
        // 如果当前字符在t中
        if (need.count(c)) {
            window[c]++;
            // 如果窗口中该字符的数量等于t中的数量
            if (window[c] == need[c]) {
                valid++;
            }
        }
        
        // 当窗口包含所有t中的字符
        while (valid == need.size()) {
            // 更新最小窗口
            if (right - left < len) {
                start = left;
                len = right - left;
            }
            
            char d = s[left];
            left++;  // 缩小窗口
            
            if (need.count(d)) {
                // 如果移除的字符使得窗口不再满足条件
                if (window[d] == need[d]) {
                    valid--;
                }
                window[d]--;
            }
        }
    }
    return len == INT_MAX ? "" : s.substr(start, len);
}
```

## 刷题记录

---

# 子串

## 子串处理技巧
子串是字符串中连续的字符序列。处理子串问题通常需要考虑：
- 子串的生成和遍历
- 字符串匹配（KMP算法）
- 回文子串
- 子串统计

**常见算法**：
- 暴力法：枚举所有子串
- 动态规划：解决回文子串等问题
- KMP算法：高效字符串匹配

## 示例代码
```cpp
// 最长回文子串 - 动态规划
string longestPalindrome(string s) {
    int n = s.size();
    if (n < 2) return s;
    
    vector<vector<bool>> dp(n, vector<bool>(n, false));
    int maxLen = 1;
    int start = 0;
    
    // 所有长度为1的子串都是回文
    for (int i = 0; i < n; i++) {
        dp[i][i] = true;
    }
    
    // 检查长度为2的子串
    for (int i = 0; i < n - 1; i++) {
        if (s[i] == s[i + 1]) {
            dp[i][i + 1] = true;
            maxLen = 2;
            start = i;
        }
    }
    
    // 检查长度大于2的子串
    for (int len = 3; len <= n; len++) {
        for (int i = 0; i <= n - len; i++) {
            int j = i + len - 1;  // 子串结束位置
            // 如果首尾字符相同且中间部分是回文
            if (s[i] == s[j] && dp[i + 1][j - 1]) {
                dp[i][j] = true;
                if (len > maxLen) {
                    maxLen = len;
                    start = i;
                }
            }
        }
    }
    
    return s.substr(start, maxLen);
}

// 重复的子字符串
bool repeatedSubstringPattern(string s) {
    int n = s.size();
    // 构造next数组
    vector<int> next(n, 0);
    for (int i = 1, j = 0; i < n; i++) {
        while (j > 0 && s[i] != s[j]) {
            j = next[j - 1];
        }
        if (s[i] == s[j]) {
            j++;
        }
        next[i] = j;
    }
    // 如果next[n-1]不为0且n能被(n - next[n-1])整除
    return next[n - 1] != 0 && n % (n - next[n - 1]) == 0;
}
```

## 刷题记录

---

# 普通数组

## 数组操作基础
数组是最基本的数据结构，元素在内存中连续存储。数组操作的核心包括：
- 排序算法（快速排序、归并排序等）
- 查找算法（二分查找）
- 数组变形（反转、旋转等）
- 数组统计（前缀和、差分数组）

**常见技巧**：
- 双指针法
- 排序后处理
- 原地修改

## 示例代码
```cpp
// 合并两个有序数组
void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
    // 从后向前合并，避免覆盖
    int i = m - 1;      // nums1的最后一个有效元素
    int j = n - 1;      // nums2的最后一个元素
    int k = m + n - 1;  // 合并后的最后一个位置
    
    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k--] = nums1[i--];
        } else {
            nums1[k--] = nums2[j--];
        }
    }
    
    // 如果nums2还有剩余元素，复制到nums1前面
    while (j >= 0) {
        nums1[k--] = nums2[j--];
    }
}

// 多数元素
int majorityElement(vector<int>& nums) {
    // Boyer-Moore投票算法
    int candidate = nums[0];
    int count = 1;
    
    for (int i = 1; i < nums.size(); i++) {
        if (count == 0) {
            candidate = nums[i];
            count = 1;
        } else if (nums[i] == candidate) {
            count++;
        } else {
            count--;
        }
    }
    
    return candidate;
}

// 旋转图像
void rotate(vector<vector<int>>& matrix) {
    int n = matrix.size();
    
    // 1. 转置矩阵
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            swap(matrix[i][j], matrix[j][i]);
        }
    }
    
    // 2. 翻转每一行
    for (int i = 0; i < n; i++) {
        reverse(matrix[i].begin(), matrix[i].end());
    }
}
```

## 刷题记录

---

# 矩阵

## 矩阵算法基础
矩阵是二维数组，在算法中常用于：
- 图像处理
- 网格问题
- 动态规划状态表示

**常见操作**：
- 矩阵转置
- 矩阵旋转
- 路径问题（动态规划）
- 岛屿问题（DFS/BFS）

## 示例代码
```cpp
// 旋转图像
void rotate(vector<vector<int>>& matrix) {
    int n = matrix.size();
    
    // 分层旋转
    for (int layer = 0; layer < n / 2; layer++) {
        int first = layer;
        int last = n - 1 - layer;
        
        for (int i = first; i < last; i++) {
            int offset = i - first;
            // 保存上边
            int top = matrix[first][i];
            // 左边 -> 上边
            matrix[first][i] = matrix[last - offset][first];
            // 下边 -> 左边
            matrix[last - offset][first] = matrix[last][last - offset];
            // 右边 -> 下边
            matrix[last][last - offset] = matrix[i][last];
            // 上边 -> 右边
            matrix[i][last] = top;
        }
    }
}

// 最大矩形
int maximalRectangle(vector<vector<char>>& matrix) {
    if (matrix.empty()) return 0;
    int m = matrix.size(), n = matrix[0].size();
    vector<int> heights(n, 0);
    int maxArea = 0;
    
    for (int i = 0; i < m; i++) {
        // 更新高度数组
        for (int j = 0; j < n; j++) {
            heights[j] = matrix[i][j] == '1' ? heights[j] + 1 : 0;
        }
        // 计算最大矩形面积
        maxArea = max(maxArea, largestRectangleArea(heights));
    }
    return maxArea;

// 辅助函数：计算直方图中的最大矩形面积
int largestRectangleArea(vector<int>& heights) {
    stack<int> s;
    heights.push_back(0);  // 哨兵
    int maxArea = 0;
    
    for (int i = 0; i < heights.size(); i++) {
        while (!s.empty() && heights[i] < heights[s.top()]) {
            int h = heights[s.top()];
            s.pop();
            int w = s.empty() ? i : i - s.top() - 1;
            maxArea = max(maxArea, h * w);
        }
        s.push(i);
    }
    return maxArea;
}
```

## 刷题记录

---

# 链表

## 链表操作基础
链表由节点组成，每个节点包含数据和指向下一个节点的指针。链表操作包括：
- 遍历链表
- 反转链表
- 检测环
- 合并有序链表

**常见技巧**：
- 虚拟头节点
- 快慢指针
- 递归处理

## 示例代码
```cpp
// 反转链表 II
ListNode* reverseBetween(ListNode* head, int left, int right) {
    if (!head || left == right) return head;
    
    ListNode dummy(0);
    dummy.next = head;
    ListNode* prev = &dummy;
    
    // 找到left的前一个节点
    for (int i = 1; i < left; i++) {
        prev = prev->next;
    }
    
    ListNode* curr = prev->next;
    ListNode* next = nullptr;
    
    // 反转从left到right的部分
    for (int i = left; i < right; i++) {
        next = curr->next;
        curr->next = next->next;
        next->next = prev->next;
        prev->next = next;
    }
    
    return dummy.next;
}

// 环形链表 II
ListNode* detectCycle(ListNode* head) {
    if (!head || !head->next) return nullptr;
    
    ListNode* slow = head;
    ListNode* fast = head;
    
    // 快慢指针检测环
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        
        if (slow == fast) {
            // 存在环，找环的入口
            slow = head;
            while (slow != fast) {
                slow = slow->next;
                fast = fast->next;
            }
            return slow;
        }
    }
    
    return nullptr;
}

// 合并K个升序链表
struct Compare {
    bool operator()(ListNode* a, ListNode* b) {
        return a->val > b->val;
    }
};

ListNode* mergeKLists(vector<ListNode*>& lists) {
    priority_queue<ListNode*, vector<ListNode*>, Compare> minHeap;
    
    // 将每个链表的头节点加入堆
    for (ListNode* list : lists) {
        if (list) {
            minHeap.push(list);
        }
    }
    
    ListNode dummy(0);
    ListNode* tail = &dummy;
    
    while (!minHeap.empty()) {
        // 取出最小值节点
        ListNode* node = minHeap.top();
        minHeap.pop();
        
        // 添加到结果链表
        tail->next = node;
        tail = tail->next;
        
        // 将该节点的下一个节点加入堆
        if (node->next) {
            minHeap.push(node->next);
        }
    }
    
    return dummy.next;
}
```

## 刷题记录

---

# 二叉树

## 二叉树遍历与操作
二叉树每个节点最多有两个子节点。主要操作包括：
- 遍历（前序、中序、后序、层序）
- 深度计算
- 路径问题
- 子树问题

**常见算法**：
- 递归遍历
- 迭代遍历（栈）
- Morris遍历
- 层次遍历（队列）

## 示例代码
```cpp
// 二叉树的层序遍历
vector<vector<int>> levelOrder(TreeNode* root) {
    vector<vector<int>> result;
    if (!root) return result;
    
    queue<TreeNode*> q;
    q.push(root);
    
    while (!q.empty()) {
        int levelSize = q.size();
        vector<int> currentLevel;
        
        for (int i = 0; i < levelSize; i++) {
            TreeNode* node = q.front();
            q.pop();
            
            currentLevel.push_back(node->val);
            
            if (node->left) q.push(node->left);
            if (node->right) q.push(node->right);
        }
        
        result.push_back(currentLevel);
    }
    
    return result;
}

// 二叉树的最大路径和
int maxPathSum(TreeNode* root) {
    int maxSum = INT_MIN;
    helper(root, maxSum);
    return maxSum;
}

int helper(TreeNode* node, int& maxSum) {
    if (!node) return 0;
    
    // 递归计算左右子树的最大路径和
    int leftMax = max(helper(node->left, maxSum), 0);
    int rightMax = max(helper(node->right, maxSum), 0);
    
    // 更新最大路径和
    maxSum = max(maxSum, node->val + leftMax + rightMax);
    
    // 返回以当前节点为根的最大路径和
    return node->val + max(leftMax, rightMax);
}

// 二叉树展开为链表
void flatten(TreeNode* root) {
    if (!root) return;
    
    // 后序遍历
    flatten(root->left);
    flatten(root->right);
    
    // 保存左右子树
    TreeNode* left = root->left;
    TreeNode* right = root->right;
    
    // 将左子树作为右子树
    root->left = nullptr;
    root->right = left;
    
    // 找到右子树的末尾
    TreeNode* current = root;
    while (current->right) {
        current = current->right;
    }
    
    // 将原来的右子树接在末尾
    current->right = right;
}
```

## 刷题记录

---

# 图论

## 图算法基础
图由顶点和边组成，图算法包括：
- 深度优先搜索（DFS）
- 广度优先搜索（BFS）
- 最短路径算法
- 拓扑排序

**常见应用**：
- 岛屿问题
- 路径问题
- 网络流
- 二分图匹配

## 示例代码
```cpp
// 岛屿数量
int numIslands(vector<vector<char>>& grid) {
    if (grid.empty()) return 0;
    int m = grid.size(), n = grid[0].size();
    int count = 0;
    
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (grid[i][j] == '1') {
                dfs(grid, i, j);
                count++;
            }
        }
    }
    return count;
}

void dfs(vector<vector<char>>& grid, int i, int j) {
    // 边界检查
    if (i < 0 || j < 0 || i >= grid.size() || j >= grid[0].size() || grid[i][j] != '1') {
        return;
    }
    
    // 标记为已访问
    grid[i][j] = '0';
    
    // 四个方向DFS
    dfs(grid, i + 1, j);
    dfs(grid, i - 1, j);
    dfs(grid, i, j + 1);
    dfs(grid, i, j - 1);
}

// 腐烂的橘子
int orangesRotting(vector<vector<int>>& grid) {
    int m = grid.size(), n = grid[0].size();
    queue<pair<int, int>> q;
    int fresh = 0;
    int time = 0;
    
    // 统计新鲜橘子，并将腐烂橘子加入队列
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (grid[i][j] == 1) {
                fresh++;
            } else if (grid[i][j] == 2) {
                q.push({i, j});
            }
        }
    }
    
    // 如果没有新鲜橘子，直接返回
    if (fresh == 0) return 0;
    
    // 四个方向
    vector<vector<int>> dirs = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
    
    while (!q.empty() && fresh > 0) {
        int size = q.size();
        
        for (int i = 0; i < size; i++) {
            auto curr = q.front();
            q.pop();
            
            for (auto dir : dirs) {
                int x = curr.first + dir[0];
                int y = curr.second + dir[1];
                
                if (x >= 0 && x < m && y >= 0 && y < n && grid[x][y] == 1) {
                    grid[x][y] = 2;
                    q.push({x, y});
                    fresh--;
                }
            }
        }
        
        if (!q.empty()) time++;
    }
    
    return fresh == 0 ? time : -1;
}

// 课程表
bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
    vector<vector<int>> adj(numCourses);
    vector<int> inDegree(numCourses, 0);
    
    // 构建邻接表和入度数组
    for (auto& pre : prerequisites) {
        adj[pre[1]].push_back(pre[0]);
        inDegree[pre[0]]++;
    }
    
    queue<int> q;
    // 将入度为0的节点加入队列
    for (int i = 0; i < numCourses; i++) {
        if (inDegree[i] == 0) {
            q.push(i);
        }
    }
    
    int count = 0;
    // 拓扑排序
    while (!q.empty()) {
        int curr = q.front();
        q.pop();
        count++;
        
        for (int neighbor : adj[curr]) {
            inDegree[neighbor]--;
            if (inDegree[neighbor] == 0) {
                q.push(neighbor);
            }
        }
    }
    
    return count == numCourses;
}
```

## 刷题记录

---

# 回溯

## 回溯算法基础
回溯通过尝试所有可能的解来解决问题，在发现当前路径不满足条件时回溯到上一步。

**关键要素**：
- 路径：当前选择的解
- 选择列表：可选的选项
- 结束条件：找到解或无法继续

**常见应用**：
- 排列组合
- 子集问题
- 棋盘问题
- 分割问题

## 示例代码
```cpp
// 全排列
vector<vector<int>> permute(vector<int>& nums) {
    vector<vector<int>> result;
    vector<int> current;
    vector<bool> used(nums.size(), false);
    backtrack(nums, used, current, result);
    return result;
}

void backtrack(vector<int>& nums, vector<bool>& used, vector<int>& current, vector<vector<int>>& result) {
    // 结束条件：当前排列完成
    if (current.size() == nums.size()) {
        result.push_back(current);
        return;
    }
    
    for (int i = 0; i < nums.size(); i++) {
        // 跳过已使用的元素
        if (used[i]) continue;
        
        // 选择元素
        used[i] = true;
        current.push_back(nums[i]);
        
        // 递归
        backtrack(nums, used, current, result);
        
        // 回溯
        current.pop_back();
        used[i] = false;
    }
}

// 子集
vector<vector<int>> subsets(vector<int>& nums) {
    vector<vector<int>> result;
    vector<int> current;
    backtrack(nums, 0, current, result);
    return result;
}

void backtrack(vector<int>& nums, int start, vector<int>& current, vector<vector<int>>& result) {
    // 添加当前子集
    result.push_back(current);
    
    for (int i = start; i < nums.size(); i++) {
        // 选择元素
        current.push_back(nums[i]);
        
        // 递归
        backtrack(nums, i + 1, current, result);
        
        // 回溯
        current.pop_back();
    }
}

// N皇后
vector<vector<string>> solveNQueens(int n) {
    vector<vector<string>> result;
    vector<string> board(n, string(n, '.'));
    solveNQueensHelper(board, 0, result);
    return result;
}

void solveNQueensHelper(vector<string>& board, int col, vector<vector<string>>& result) {
    if (col == board.size()) {
        result.push_back(board);
        return;
    }
    
    for (int row = 0; row < board.size(); row++) {
        if (isSafe(board, row, col)) {
            board[row][col] = 'Q';
            solveNQueensHelper(board, col + 1, result);
            board[row][col] = '.';
        }
    }
}

bool isSafe(vector<string>& board, int row, int col) {
    int n = board.size();
    
    // 检查上方
    for (int i = 0; i < row; i++) {
        if (board[i][col] == 'Q') return false;
    }
    
    // 检查左上对角线
    for (int i = row, j = col; i >= 0 && j >= 0; i--, j--) {
        if (board[i][j] == 'Q') return false;
    }
    
    // 检查右上对角线
    for (int i = row, j = col; i >= 0 && j < n; i--, j++) {
        if (board[i][j] == 'Q') return false;
    }
    
    return true;
}
```
## 刷题记录

---

# 二分查找

## 二分查找算法
二分查找在有序数组中查找特定元素，时间复杂度为O(log n)。

**基本步骤**：
1. 确定查找范围
2. 计算中间位置
3. 比较中间元素与目标值
4. 根据比较结果缩小查找范围

**变种**：
- 查找第一个/最后一个目标值
- 查找插入位置
- 旋转数组查找

## 示例代码
```cpp
// 搜索旋转排序数组
int search(vector<int>& nums, int target) {
    int left = 0, right = nums.size() - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (nums[mid] == target) {
            return mid;
        }
        
        // 判断哪一部分是有序的
        if (nums[left] <= nums[mid]) {
            // 左半部分有序
            if (nums[left] <= target && target < nums[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        } else {
            // 右半部分有序
            if (nums[mid] < target && target <= nums[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    return -1;
}

// 在排序数组中查找元素的第一个和最后一个位置
vector<int> searchRange(vector<int>& nums, int target) {
    vector<int> result = {-1, -1};
    
    // 查找第一个位置
    int left = 0, right = nums.size() - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    if (left < nums.size() && nums[left] == target) {
        result[0] = left;
    } else {
        return result;
    }
    
    // 查找最后一个位置
    right = nums.size() - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] <= target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    result[1] = right;
    
    return result;
}

// 寻找峰值
int findPeakElement(vector<int>& nums) {
    int left = 0, right = nums.size() - 1;
    
    while (left < right) {
        int mid = left + (right - left) / 2;
        
        if (nums[mid] > nums[mid + 1]) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    
    return left;
}
```
## 刷题记录

---

# 栈

## 栈的应用
栈是一种后进先出（LIFO）的数据结构，主要应用包括：
- 括号匹配
- 表达式求值
- 单调栈
- 最小栈

**常见操作**：
- push：入栈
- pop：出栈
- top：获取栈顶元素
- empty：判断栈是否为空

## 示例代码
```cpp
// 有效的括号
bool isValid(string s) {
    stack<char> st;
    
    for (char c : s) {
        if (c == '(' || c == '[' || c == '{') {
            st.push(c);
        } else {
            if (st.empty()) return false;
            
            char top = st.top();
            st.pop();
            
            if (c == ')' && top != '(') return false;
            if (c == ']' && top != '[') return false;
            if (c == '}' && top != '{') return false;
        }
    }
    
    return st.empty();
}

// 最小栈
class MinStack {
private:
    stack<int> st;
    stack<int> minSt;
    
public:
    MinStack() {}
    
    void push(int val) {
        st.push(val);
        if (minSt.empty() || val <= minSt.top()) {
            minSt.push(val);
        }
    }
    
    void pop() {
        if (st.top() == minSt.top()) {
            minSt.pop();
        }
        st.pop();
    }
    
    int top() {
        return st.top();
    }
    
    int getMin() {
        return minSt.top();
    }
};

// 下一个更大元素 I
vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
    stack<int> st;
    unordered_map<int, int> nextGreater;
    
    // 从右到左遍历nums2
    for (int i = nums2.size() - 1; i >= 0; i--) {
        while (!st.empty() && st.top() <= nums2[i]) {
            st.pop();
        }
        
        if (!st.empty()) {
            nextGreater[nums2[i]] = st.top();
        } else {
            nextGreater[nums2[i]] = -1;
        }
        
        st.push(nums2[i]);
    }
    
    vector<int> result;
    for (int num : nums1) {
        result.push_back(nextGreater[num]);
    }
    
    return result;
}
```
## 刷题记录
---

# 堆

## 堆的应用
堆是一种特殊的完全二叉树，分为最大堆和最小堆。主要应用包括：
- 优先队列
- Top K问题
- 数据流中的中位数
- 合并有序序列

**常见操作**：
- 插入元素：O(log n)
- 删除堆顶：O(log n)
- 获取堆顶：O(1)

## 示例代码
```cpp
// 数据流中的第K大元素
class KthLargest {
private:
    priority_queue<int, vector<int>, greater<int>> pq;
    int k;
    
public:
    KthLargest(int k, vector<int>& nums) {
        this->k = k;
        for (int num : nums) {
            add(num);
        }
    }
    
    int add(int val) {
        pq.push(val);
        if (pq.size() > k) {
            pq.pop();
        }
        return pq.top();
    }
};

// 前K个高频元素
vector<int> topKFrequent(vector<int>& nums, int k) {
    unordered_map<int, int> frequency;
    for (int num : nums) {
        frequency[num]++;
    }
    
    // 小顶堆，频率低的在堆顶
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
    
    for (auto& entry : frequency) {
        pq.push({entry.second, entry.first});
        if (pq.size() > k) {
            pq.pop();
        }
    }
    
    vector<int> result;
    while (!pq.empty()) {
        result.push_back(pq.top().second);
        pq.pop();
    }
    
    return result;
}

// 滑动窗口最大值
vector<int> maxSlidingWindow(vector<int>& nums, int k) {
    vector<int> result;
    deque<int> dq; // 双端队列，存储索引
    
    for (int i = 0; i < nums.size(); i++) {
        // 移除不在窗口内的元素
        while (!dq.empty() && dq.front() <= i - k) {
            dq.pop_front();
        }
        
        // 移除比当前元素小的元素
        while (!dq.empty() && nums[dq.back()] < nums[i]) {
            dq.pop_back();
        }
        
        dq.push_back(i);
        
        // 窗口大小达到k时，记录最大值
        if (i >= k - 1) {
            result.push_back(nums[dq.front()]);
        }
    }
    
    return result;
}
```

## 刷题记录
---

# 贪心算法

## 贪心算法原理
贪心算法在每一步选择当前最优解，期望最终得到全局最优解。

**特点**：
- 局部最优选择
- 无后效性
- 贪心选择性质

**常见应用**：
- 区间调度问题
- 活动选择问题
- Huffman编码
- 最小生成树

## 示例代码
```cpp
// 跳跃游戏
bool canJump(vector<int>& nums) {
    int maxReach = 0;
    int n = nums.size();
    
    for (int i = 0; i < n; i++) {
        // 如果当前位置可达
        if (i <= maxReach) {
            // 更新最远可达位置
            maxReach = max(maxReach, i + nums[i]);
            // 如果可以到达终点
            if (maxReach >= n - 1) {
                return true;
            }
        } else {
            return false;
        }
    }
    
    return maxReach >= n - 1;
}

// 加油站
int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
    int totalGas = 0;
    int totalCost = 0;
    int currentGas = 0;
    int start = 0;
    
    for (int i = 0; i < gas.size(); i++) {
        totalGas += gas[i];
        totalCost += cost[i];
        currentGas += gas[i] - cost[i];
        
        // 如果当前油量为负，重置起点
        if (currentGas < 0) {
            start = i + 1;
            currentGas = 0;
        }
    }
    
    return totalGas >= totalCost ? start : -1;
}

// 摆动排序 II
void wiggleSort(vector<int>& nums) {
    // 排序数组
    sort(nums.begin(), nums.end());
    
    vector<int> temp = nums;
    int n = nums.size();
    int left = (n + 1) / 2 - 1;  // 中间位置
    int right = n - 1;            // 末尾位置
    
    // 交替放置较大和较小的数
    for (int i = 0; i < n; i++) {
        if (i % 2 == 0) {
            nums[i] = temp[left--];
        } else {
            nums[i] = temp[right--];
        }
    }
}
```

## 刷题记录

---

# 动态规划

## 动态规划基础
动态规划通过将问题分解为重叠的子问题，存储子问题的解来避免重复计算。

**关键要素**：
- 状态定义
- 状态转移方程
- 初始化条件
- 结果输出

**常见模式**：
- 一维DP
- 二维DP
- 背包问题
- 路径问题

## 示例代码
```cpp
// 爬楼梯
int climbStairs(int n) {
    if (n <= 2) return n;
    
    vector<int> dp(n + 1);
    dp[1] = 1;
    dp[2] = 2;
    
    for (int i = 3; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    
    return dp[n];
}

// 零钱兑换
int coinChange(vector<int>& coins, int amount) {
    vector<int> dp(amount + 1, amount + 1);
    dp[0] = 0;
    
    for (int i = 1; i <= amount; i++) {
        for (int coin : coins) {
            if (coin <= i) {
                dp[i] = min(dp[i], dp[i - coin] + 1);
            }
        }
    }
    
    return dp[amount] > amount ? -1 : dp[amount];
}

// 最长递增子序列
int lengthOfLIS(vector<int>& nums) {
    int n = nums.size();
    if (n == 0) return 0;
    
    vector<int> dp(n, 1);
    int maxLength = 1;
    
    for (int i = 1; i < n; i++) {
        for (int j = 0; j < i; j++) {
            if (nums[i] > nums[j]) {
                dp[i] = max(dp[i], dp[j] + 1);
            }
        }
        maxLength = max(maxLength, dp[i]);
    }
    
    return maxLength;
}

// 编辑距离
int minDistance(string word1, string word2) {
    int m = word1.size();
    int n = word2.size();
    
    vector<vector<int>> dp(m + 1, vector<int>(n + 1));
    
    // 初始化
    for (int i = 0; i <= m; i++) {
        dp[i][0] = i;
    }
    for (int j = 0; j <= n; j++) {
        dp[0][j] = j;
    }
    
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (word1[i - 1] == word2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                dp[i][j] = min({dp[i - 1][j], dp[i][j - 1], dp[i - 1][j - 1]}) + 1;
            }
        }
    }
    
    return dp[m][n];
}
```

## 刷题记录

---

# 多维动态规划

## 多维DP问题
多维动态规划涉及二维或更高维的状态空间，常用于解决复杂问题。

**常见问题类型**：
- 二维网格路径问题
- 字符串编辑问题
- 区间DP问题
- 树形DP问题

**优化技巧**：
- 状态压缩
- 滚动数组
- 空间优化

## 示例代码
```cpp
// 最长公共子序列
int longestCommonSubsequence(string text1, string text2) {
    int m = text1.size();
    int n = text2.size();
    
    vector<vector<int>> dp(m + 1, vector<int>(n + 1));
    
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (text1[i - 1] == text2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1] + 1;
            } else {
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
    }
    
    return dp[m][n];
}

// 不同路径 II
int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
    int m = obstacleGrid.size();
    int n = obstacleGrid[0].size();
    
    vector<vector<long long>> dp(m, vector<long long>(n, 0));
    
    // 初始化起点
    if (obstacleGrid[0][0] == 0) {
        dp[0][0] = 1;
    }
    
    // 初始化第一行
    for (int j = 1; j < n; j++) {
        if (obstacleGrid[0][j] == 0) {
            dp[0][j] = dp[0][j - 1];
        }
    }
    
    // 初始化第一列
    for (int i = 1; i < m; i++) {
        if (obstacleGrid[i][0] == 0) {
            dp[i][0] = dp[i - 1][0];
        }
    }
    
    // 填充DP表
    for (int i = 1; i < m; i++) {
        for (int j = 1; j < n; j++) {
            if (obstacleGrid[i][j] == 0) {
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
    }
    
    return dp[m - 1][n - 1];
}

// 交错字符串
bool isInterleave(string s1, string s2, string s3) {
    int m = s1.size();
    int n = s2.size();
    int k = s3.size();
    
    if (m + n != k) return false;
    
    vector<vector<bool>> dp(m + 1, vector<bool>(n + 1));
    
    for (int i = 0; i <= m; i++) {
        for (int j = 0; j <= n; j++) {
            if (i == 0 && j == 0) {
                dp[i][j] = true;
            } else if (i == 0) {
                dp[i][j] = dp[i][j - 1] && (s2[j - 1] == s3[i + j - 1]);
            } else if (j == 0) {
                dp[i][j] = dp[i - 1][j] && (s1[i - 1] == s3[i + j - 1]);
            } else {
                dp[i][j] = (dp[i - 1][j] && s1[i - 1] == s3[i + j - 1]) ||
                           (dp[i][j - 1] && s2[j - 1] == s3[i + j - 1]);
            }
        }
    }
    
    return dp[m][n];
}
```

## 刷题记录

---

# 技巧

## 常用编程技巧
总结一些常用的编程技巧和优化方法。

**技巧分类**：
- 前缀和与差分数组
- 位运算技巧
- 快速幂
- 离散化

**优化方法**：
- 空间优化
- 时间优化
- 代码简洁性优化

## 示例代码
```cpp
// 前缀和与差分数组
vector<int> prefixSum(vector<int>& nums) {
    vector<int> prefix(nums.size() + 1, 0);
    for (int i = 0; i < nums.size(); i++) {
        prefix[i + 1] = prefix[i] + nums[i];
    }
    return prefix;
}

// 使用前缀和计算区间和
int rangeSum(vector<int>& prefix, int left, int right) {
    return prefix[right + 1] - prefix[left];
}

// 差分数组
vector<int> differenceArray(vector<int>& nums) {
    vector<int> diff(nums.size() + 1, 0);
    for (int i = 0; i < nums.size(); i++) {
        diff[i] += nums[i];
        if (i + 1 < nums.size()) {
            diff[i + 1] -= nums[i];
        }
    }
    return diff;
}

// 快速幂
long long fastPow(long long x, long long n) {
    long long result = 1;
    while (n > 0) {
        if (n % 2 == 1) {
            result *= x;
        }
        x *= x;
        n /= 2;
    }
    return result;
}

// 位运算技巧
// 判断奇偶
bool isOdd(int n) {
    return n & 1;
}

// 交换两个数（不使用临时变量）
void swap(int& a, int& b) {
    a ^= b;
    b ^= a;
    a ^= b;
}

// 计算二进制中1的个数
int countBits(int n) {
    int count = 0;
    while (n) {
        count += n & 1;
        n >>= 1;
    }
    return count;
}

// 离散化
vector<int> discretization(vector<int>& nums) {
    vector<int> sorted = nums;
    sort(sorted.begin(), sorted.end());
    sorted.erase(unique(sorted.begin(), sorted.end()), sorted.end());
    
    vector<int> result;
    for (int num : nums) {
        result.push_back(lower_bound(sorted.begin(), sorted.end(), num) - sorted.begin());
    }
    return result;
}
```

## 刷题记录


---
