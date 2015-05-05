Iterator 與 Generator

```
在《Design Patterns: Elements of Reusable Object-Oriented Software》書中，定義了迭代器模式：「提供一種循序（Sequentially）存取聚集（aggregate）物件，但又不曝露底層細節的方式。」Java定義Iterator或Iterable等，正是傳統迭代器的基本實現。

(src: 從具體到抽象的迭代器)
```

```
迭代器是设计模式的一种，迭代器的核心方法是 hasNext 和 next ，hasNext判断函数内部有没有下一个变量，next代表偏移到下一个变量，并且返回结果

迭代器的应用场景在于：屏蔽数据结构集合的各种差异，对于接口只要实现了hasNext和next 的api，就可以成功处理各种结果。

(src:异步的那些事儿，es6)
```

```
回到es6标准当中，引入了Generator函数，Generator是一个普通函数，但是有两个特征，1，在function命令到函数名之间有一个星号，2.函数内可以使用yield语句，通过yield把结果抛出来。


(src:异步的那些事儿，es6)
```

```
所谓Generator，有多种理解角度。首先，可以把它理解成一个函数的内部状态的遍历器，每调用一次，函数的内部状态发生一次改变（可以理解成发生某些事件）。ES6引入Generator函数，作用就是可以完全控制函数的内部状态的变化，依次遍历这些状态。

在形式上，Generator是一个普通函数，但是有两个特征。一是，function命令与函数名之间有一个星号；二是，函数体内部使用yield语句，定义遍历器的每个成员，即不同的内部状态（yield语句在英语里的意思就是“产出”）。


(src:Generator 函数)
```





### 參考資料
1. http://openhome.cc/Gossip/DesignPattern/IteratorPattern.htm
2. [异步的那些事儿，es6](http://www.jianshu.com/p/fb27831af7ff)
3. [從具體到抽象的迭代器](http://www.ithome.com.tw/node/77727)
4. [Generator 函数](http://es6.ruanyifeng.com/#docs/generator)
5. [Generator 函数的含义与用法](http://www.ruanyifeng.com/blog/2015/04/generator.html)
