# Pattern 1 ： Factory Method Design pattern 工厂设计模式

## Summary——概述

**工厂方法设计模式**是简单工厂设计模式的进化版。前面提到，简单工厂模式有着不满足开闭原则的巨大缺陷。而工厂方法模式只需要创建一个继承自工厂接口的类来创建产品，让其符合开闭原则即可。

## Why——为什么要使用工厂方法模式

我们先考虑之前讨论过的简单工厂模式。当我需要添加一个新的产品类的时候，我们势必需要修改原有的工厂类的方法，在其中加上判断、创建新类的语句——而在面向对象的设计中，有一个非常重要的设计原则，即开闭原则：对扩展开放，对修改关闭。意思就是在**设计程序时尽量设计成增加其他的类，而不用去修改原有的类**。

为了弥补简单方法的这一不足，我们使用工厂方法模式。

---

## How——如何实现工厂方法模式

对简单工厂模式进行修改如下：

<!-- 插入图片 -->

在这里，原先的工厂类成为了一个接口，而每一个产品的具体实现放在了继承这个接口的具体工厂中。每一个具体的工厂生产一种产品。

在这种模式下，如果需要增加一种新的产品，只需要创建一个新的工厂类，让其继承总的工厂接口，然后在其中写出生产产品的工厂方法即可。

---

## WHEN——何时使用工厂模式

作为一种创建类模式，在任何需要生成复杂对象的地方，都可以使用工厂方法模式。有一点需要注意的地方就是复杂对象适合使用工厂模式，而简单对象，特别是只需要通过 new 就可以完成创建的对象，无需使用工厂模式。如果使用工厂模式，就需要引入一个工厂类，会增加系统的复杂度。

## 结语

工厂模式是一种非常常用的设计模式。在较为小型的项目中可能体会不到工厂模式的优点。但是一旦项目扩大，工厂模式就成为一种必不可少的创建实例的方式。正如工业革命建造了无数工厂极大地提高了生产力，从而使大批量生产工业产品变得可能一样，工厂模式的出现使得软件系统的扩展性更强，可维护性更高，因此使得管理庞大的项目变得可能。