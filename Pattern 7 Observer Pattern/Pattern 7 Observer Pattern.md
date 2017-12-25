### Pattern 7: Observer Pattern  观察者模式

#### Summary——概述

**观察者模式**Observer Pattern）属于行为型模式。类的行为随着观察到别的类的改变而改变。
在观察者模式中，定义了对象间的一种一对多的组合关系，一个对象的状态发生变化时，所有依赖于它的对象都得到通知并自动刷新。

---

#### Example——观察者模式的例子

观察者模式通常是多个观察者关注一个被观察者，当被观察者更改信息的时候，观察者会得到通知，并更新数据。

现在有一个智能水杯，它能够读取数据他其中盛放的水温数据，而这些水温数据可以被三个不同的液晶屏幕显示，显示的单位分别为：摄氏度、华氏度、开尔文。通过观察者模式，我们希望水杯自身能够生成一个温度数据，当水杯的水温发生改变的时候，发送通知给显示模块，然后所有显示模块根据这个温度数据进行换算。

将上述描述转化为UML类图：

<center>

![图7-1 水杯的观察者模式](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%207%20Observer%20Pattern/7-1.png)

</center>

上述的模型就是观察者的UML类图。我们首先可以看到有一个Observer接口，这个接口在Java中已经有具体的实现。所有显示的GUI界面都继承自这个接口，表示他们都是Observer的子类，都属于观察者。Observable代表的是被观察的对象，而水温数据是被观察的数据，读取水温的对象继承自Observable。当水温数据改变时，通知所有观察者改变的数据。

---

#### Why——为什么要使用观察者模式

抽象上述的类图，使其一般化：

![图7-2 一般的观察者模式](https://raw.githubusercontent.com/Jannchie/Software-Design-Pattern-Note/master/Pattern%207%20Observer%20Pattern/7-2.png)

可以看出观察者模式的优点主要在于：观察者模式能够分离显示界面和数据读取的业务处理模块。