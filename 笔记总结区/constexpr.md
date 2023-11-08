# constexpr(c++11/14)

**常量表达式**

* C++ 标准中数组的长度必须是一个常量表达式
* constexpr修饰的函数，只能有一个return语句，不可有其他非编译期语句

    ```cpp
    constexpr int fibonacci(const int n) {
        return n == 1 || n == 2 ? 1 : fibonacci(n-1)+fibonacci(n-2);
    }
    ```

* 从 **C++14** 开始，constexpr 函数可以在内部使用局部变量、循环和分支等简单语句

    ```cpp
    constexpr int fibonacci(const int n) {
        if(n == 1) return 1;
        if(n == 2) return 1;
        return fibonacci(n-1) + fibonacci(n-2);
    }
    ```

* const与constexpr的区别：
  * const 变量的初始化可以延迟到运行时，而 constexpr 变量必须在编译时进行初始化。所有 constexpr 变量必须使用常量表达式初始化。
  * 修饰指针的不同：
    * 在使用const时，如果关键字const出现在星号左边，表示被指物是常量；如果出现在星号右边，表示指针本身是常量；如果出现在星号两边，表示被指物和指针两者都是常量。与const不同，在constexpr声明中如果定义了一个指针，限定符constexpr仅对指针有效，与指针所指对象无关。
