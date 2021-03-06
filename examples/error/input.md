错误处理（error handling）是处理可能发生失败情况的过程。例如读取一个文件失败，然后继续使用这个**失效的**输入显然是有问题的。错误处理允许我们以一种显式的方式来发现并处理这类错误，避免了其余代码发生潜在的问题。

我们将要看到的最简单的错误处理机制就是 `panic`。它会打印一个错误消息，开始展开任务（译注：感觉此句翻译不好，望指正，原文为 starts unwinding the task），且通常退出程序。考虑下面的实例：

{error.play}

这表明我们可以根据自己的想法来引发程序失败，但会出现一个问题：要是公主（princess）**没**得到礼物会发生什么？就像处理蛇那样的方式，我们**可以**针对空字符串（`""`）的检查进行显式地测试。问题在于程序员并没有习惯测试这些检查，除非编译器指出这些检查是必需的。

为了使这变得更可靠，我们需要编译器指出可能没有礼物的情形。在本章，我们将学习使用 `Option` 来应对这种情况，以及各种各样的函数来处理 `Option` 的一个或多个用法的结果。
