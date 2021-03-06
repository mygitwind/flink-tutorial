# 第七章，有状态算子和应用

状态操作符和用户自定义函数都是我们在写流处理程序时，常用的工具。事实上，大部分稍微复杂一点的逻辑都需要保存数据或者保存计算结果。很多Flink内置的操作符例如：source操作符，sink操作符等等都是有状态的，也就是说会缓存流数据或者计算结果。例如，窗口操作符将会为ProcessWindowFunction收集输入的数据，或者收集ReduceFunction计算的结果。而ProcessFunction也会保存定时器事件，一些sink方法为了做到exactly-once，会将事务保存下来。除了内置的操作符以及提供的source和sink操作符，Flink的DataStream API还在UDF函数中暴露了可以注册、保存和访问状态的接口。

本章重点讨论有状态的用户自定义函数的实现，以及讨论有状态应用的性能和健壮性。特别的，我们将解释在用户自定义函数中，如何定义不同类型的状态，以及如何与状态进行交互。我们还讨论了性能方面的问题以及如何控制状态大小的问题。

