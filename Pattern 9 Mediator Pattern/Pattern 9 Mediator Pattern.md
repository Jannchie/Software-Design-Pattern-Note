### Pattern 9: Mediator Pattern  中介者模式

#### Summary——概述

**中介者模式**（Visitor Pattern）属于行为型模式。多个实体需要相互通信是一种非常复杂的情况，通过使用一个专门的中介类进行通信的处理是一种更加科学的方案。中介者模式通过一个中介对象封装多个实体的具体交互过程，从而能够减少多个通信实体之间的耦合，进而提高系统的复用性与可维护性。

---

#### Example——中介者模式的例子

中介者顾名思义，就是扮演了一个多个人之间的一个中间人的角色，或者说是作为多个实体之间的媒介。现在的中介最常见于买房时的房产中介。如果我们考虑买房，我们是否会去房产公司一家一家地了解他们提供的房屋的价格、户型、地段等信息？我想大概不会。同样的，房产公司想要让他的房子能让更多的人知道，他们也不会挨家挨户地询问是否有购买者愿意买他们的房子。我们常常会去房产中介哪儿看一下哪些房型可以选择，而房产公司会把自己的房型提供给中介展示。在这里中介就是买方和卖方的中介者。买方通过中介了解房屋的售卖信息，可以不需要逛大量的房产公司，而卖方也通过中介，从而不需要挨家挨户地询问是否要买房。

---

#### Analysis——中介者模式的分析

在只有两个参与者的时候，双方都依赖于对方，他们之间的通信还是非常简单的，但是在我们添加参与者的类的时候，问题就出现了。

<center>

![图9-1 不使用中介者](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%209%20Mediator%20Pattern/9-1.png)

</center>

比如在买房的同时，我们需要考虑装修的问题，于是我们需要添加一个“装修公司”类，用户需要联系装修公司，而装修公司又要根据具体的户型提出报价。因此，我们需要对房产公司和用户动刀，添加用户联系房产公司的方法与房产公司获取房产信息的方法，如果我们要再加其他参与者呢？每当添加一次都要对更多的类进行修改，这显然是不合理的。因此我们需要使用中介者模式。

<center>

![图9-2 中介者模式](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%209%20Mediator%20Pattern/9-2.png)

</center>

中介者模式的特征是使用了一个中介类来封装多个实体的具体交互过程，还是拿之前的例子，中介者能够收集房产的信息、买家的信息，在这个例子里，还能收集装修公司的信息。此时对于各个实体而言，他们只需要与同一个中介者交互即可，用户如果需要房产的信息，他会去咨询中介，装修公司如果需要户型的信息来估计价格和工时，也可以通过中介去查询。

而常见的中介者模式类图是类似这样的：

<center>

![图9-3 一般的中介者模式](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%209%20Mediator%20Pattern/9-3.png)

</center>

在中介者模式中，一般称互相有联系的实体为同事（Colleague），他们可以看做继承了同事类。所有同事依赖于中介者（Mediator），也就是说他们知道中介者的存在，可以调用中介者之中的方法。而具体的中介者依赖于同事类，可以从同事类中获取信息供其他同事类去使用。

#### Evaluation——访问者模式的评估

中介者模式的优点是显而易见的，通过中介者能够更加从容地组织起多个实体之间的消息传递与通信。通过采用中介者模式能够极大地减少对象之间的关系数量。对多个对象解耦。

中介者模式的缺点也同样明显，从上述类图就可以看出，中介者类由于处理了多个对象之间的通信，致使中介者中必须实现大量的交互方法，显得非常臃肿，可维护性不高。