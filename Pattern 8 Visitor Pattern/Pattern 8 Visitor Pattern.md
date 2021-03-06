### Pattern 8: Visitor Pattern  访问者模式

#### Summary——概述

**访问者模式**（Visitor Pattern）属于行为型模式。访问者模式的意义在于能够使数据的存储与数据的使用分离。当我们需要访问的数据不会经常改变，然而对数据的操作经常发生变化时，我们需要使用访问者模式。

---

#### Example——访问者模式的例子

场景是我们要去店里买东西，每一样商品都有它的价格。对于每一件商品而言，它只知道自己有价格而已。如果有普通顾客来买东西，他同时看中了好几个商品，则需要计算这些商品的总价格。那么又有一个VIP顾客过来买，他买所有东西打八折，那么计算的方法就会有所不同。同样，节假日打折、满减优惠、清仓大甩卖等等，不同的促销策略都需要不同的方式处理这些数据。那么问题来了，处理这些数据的方法应该放在哪里呢？放在每一个商品类中明显是非常不科学不合理的。首先这种计算价格并统计的方法就不应该是一个商品应该拥有的方法，这便会产生接口污染。其次，打折的方案是非常不稳定的，可能经常发生变化，双十一和双十二的打折策略可能完全不同，而同时，商品本身的价格却是相对稳定的。我们可以看到，对于这个例子而言，数据的存储结构不怎么变化，而对数据的操作经常发生变化，因此我们需要对操作和存储解耦，分离出经常需要变化的部分。

<center>

![图8-1 访问者模式的例子](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%208%20Visitor%20Pattern/8-1.png)

</center>

上述的模型就是刚才所描述的情形的UML类图。我们可以看到商品是一个超类，他有商品A和商品B两个子类，作为商品，他们只有自身的价格。而此时顾客成为一个访问者去访问这些商品。对于不同时间状态下的顾客，他们购买不同商品对应的价格也有所不同。顾客通过调用商品的获得价格方法来取得商品的价格，再进行计算，从而获得最终的价格。

---

抽象上述的例子，我们可以得到一般的访问者模式的UML类图：

<center>

![图8-2 一般的访问者模式](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%208%20Visitor%20Pattern/8-2.png)

</center>

我们可以看到这个类图和上面的例子还是有所不同的，不同的地方主要有两个，一个所有访问者多了一个父类，一个是被访问者多了一个accept方法。accept方法的目的是接待访问者，参数是超类Visitor。每当一个访问者来访问时，将访问者以超类的形式传入，从而可以接待不同的访问者，传入后，再调用对应访问者访问自身的方法。

#### Evaluation——访问者模式的评估

访问者模式的优点在于扩展性较强，至少添加一个新的被访问者还是很简单的。访问者模式还能够实现数据存储与数据使用的解耦，这是访问者模式最为主要和关键的作用。但是访问者模式并不满足依赖倒转原则——编写访问者类的时候，我们是面向实体类编程而不是面向接口编程的，这将导致如果被访问者较多，写一个新的访问者还是需要添加极多的代码。