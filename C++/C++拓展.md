
![[assets/file-20251005141848823.png]]
# - namespace Utils： 
- 这是 命名空间定义，用于将代码逻辑分组，避免全局命名冲突。
- 例子中定义的三个函数被封装在 Utils 命名空间下。
## - inline 关键字的作用： 
- 主要目的： 
- 编译期函数内联：通过 inline 关键字告诉编译器 建议将函数内联展开（将函数体直接嵌入调用处），减少函数调用开销（例如压栈、跳转等操作），提升性能。
- 避免链接错误：当函数在头文件中定义且被多个源文件包含时，如果没有 inline 修饰，会导致 multiple definition 错误。添加 inline 后，允许该函数在多个编译单元中存在同一定义。
## - 关键特性： 
- 现代编译器会自动决定是否内联，并非强制要求（即使未加 inline，编译器可能也会优化）。
- 代码中的具体应用： 
- 示例中三个工具函数（constrain、add、sub）被声明为 inline，说明两点：
- 这些函数可能被频繁调用，需要 性能优化。
- 它们在头文件中定义，且可能被多个 .cpp 文件包含，需通过 inline 避免重复定义错误。

# 指针数组与数组指针
| 特性                  | 指针数组（Array of Pointers） | 数组指针（Pointer to an Array）      |
| ------------------- | ----------------------- | ------------------------------ |
| 定义                  | 数组元素都是指针                | 一个指针指向整个数组                     |
| 语法	Type* Name[Size] | （*在类型后，无括号）             | Type (*Name)[Size]（*在数组名前，有括号） |
| 内存结构                | 多个独立指针存放在连续内存中          | 单个指针指向一个连续数组                   |
| 典型用途                | 管理多个独立对象（如字符串数组）        | 操作多维数组（如二维数组的行操作）              |
## 指针数组示例
```cpp
// 指针数组：每个元素是 char* 类型的指针
const char* colors[3] = { 
    "Red",    // 每个指针指向独立的字符串常量
    "Green",
    "Blue"
};

// 访问方式
cout << colors[0];  // 输出 "Red"
cout << *colors[1]; // 输出 'G'（通过指针解引用）

```
## 数组指针示例
```cpp
// 二维数组
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};

// 数组指针：指向包含3个int的数组
int (*rowPtr)[3] = matrix; // 指向第一行 {1,2,3}

// 遍历第一行
for (int i = 0; i < 3; i++) {
    cout << (*rowPtr)[i] << " ";  // 输出 1 2 3
}

// 移动到第二行
rowPtr++;  
for (int i = 0; i < 3; i++) {
    cout << (*rowPtr)[i] << " ";  // 输出 4 5 6
}

```
## 关键区别总结
- 指针数组适用于管理多个独立对象（如不同长度的字符串）。
- 数组指针适用于操作多维数组的连续内存块（如按行遍历二维数组）。

# explicit关键词

![[assets/file-20251005144631766.png]]

explicit：禁止隐式类型转换（防止从字符串或标签意外构造对象）。
初始化列表：调用基类 Device 的构造函数，并初始化成员变量 brake 和 motor 为 NULL。

# 指针函数与函数指针
- 指针函数：是指返回指针的函数。简单来说，指针函数执行完函数体内的代码后，会返回一个指针作为结果。
- 函数指针：是指向函数的指针。函数指针可以存储函数的地址，通过函数指针可以调用该函数。
## 指针函数示例
```cpp
#include <stdlib.h>

// 定义一个指针函数，该函数接受一个整数参数，返回指向整型的指针
int* allocateArray(int size) {
    return (int*)malloc(size * sizeof(int));
}

int main() {
    int* array = allocateArray(10); // 调用指针函数，分配一个包含10个整数的数组
    if (array != NULL) {
        // 如果分配成功，可以使用这个数组
        array[0] = 1;
        array[1] = 2;
        // ...
        free(array); // 使用完后释放内存
    }
    return 0;
}

```

## 函数指针示例
```cpp
#include <stdio.h>

// 定义两个函数
int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int main() {
    // 定义一个函数指针，指向接受两个整数参数并返回一个整数的函数
    int (*operation)(int, int);

    // 根据需要选择不同的函数
    operation = &add; // 或者直接写 operation = add;
    int result = operation(5, 3);
    printf("5 + 3 = %d\n", result); // 输出 8

    operation = &subtract; // 或者直接写 operation = subtract;
    result = operation(5, 3);
    printf("5 - 3 = %d\n", result); // 输出 2

    return 0;
}

```

	这两个示例展示了指针函数和函数指针的不同之处，一个是函数返回指针，一个是使用指针来指向函数。