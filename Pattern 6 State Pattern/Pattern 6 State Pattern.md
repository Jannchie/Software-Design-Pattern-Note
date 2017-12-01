## Pattern 6: State Pattern  状态模式

### Summary——概述

**状态模式**（State Pattern）属于行为型模式。类的行为随着状态的改变而改变。
在状态模式中，我们需要创建表示各种状态的对象和一个行为随着状态对象改变而改变的 context 对象。

---

### Example——状态模式的例子

有一些类的状态会发生改变，在不同的状态下，类的行为也会发生变化。比如图书馆的一本书，在没有人借走它的情况下，它拥有被借走的方法。而一旦被人借走，它就不再能被借出，同时拥有了被归还的方法。

将上述描述转化为UML类图：

<center>

![图6-1 图书状态模式](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%206%20State%20Pattern/6-1.png)

</center>

上述的模型就是采用状态模式的UML类图。图书可以拥有一个状态的接口，从而可以实现不同状态下的不同功能。当图书没被借走时，状态为notBorrowed，此时可以实现借书borrowTheBook的方法。而当图书被借走后，可以实现returnTheBook的方法。

---

### Why——为什么要使用状态模式

抽象上述的类图，使其一般化：

![图6-2 图书状态模式](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%206%20State%20Pattern/6-2.png)

可以看出状态模式的优点：

- 状态模式使得对象的行为依赖于它的状态（属性），并且可以根据它的状态改变而改变它的相关行为。
- 当操作带有大量与状态相关的、多部分的条件语句时，使用状态模式能够轻松地组织起来。
- 客户对象先创建一个具体的状态类的对象，然后，在创建Context对象的时候，通过参数传递给Context对象。此后，客户程序就不必与该状态对象直接交互。
- 可扩展性好，当要修改某个状态子类的时候，不需要修改客户类与Context类；当要添加一个新的状态子类的时候，不需要修改客户类与Context类，只需要少许修改状态子类的changeState方法。


---

### Disadvantage——状态模式的缺点

当然策略模式也不是完美的，主要的缺点在于：状态模式对"开闭原则"的支持并不太好，对于可以切换状态的状态模式，增加新的状态类需要修改那些负责状态转换的源代码，否则无法切换到新增状态，而且修改某个状态类的行为也需修改对应类的源代码。