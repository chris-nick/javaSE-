## Java面试基础一（推荐书籍Java Programming Interview Exposed）
  1.  String、StringBuilder、StringBuffer的区别.<br/>
    &nbsp;String:不可变对象,String s = &nbsp;"123";s=s+4;//结果是"1234",实际JVM创建了两个对象,第一个对象被赋值"123",第二个对象执行s+4后第一个对象会被GC.<br/>
    &nbsp;StringBuilder和StringBuffer:对象可变,StringBuiler sb = new &nbsp;StringBuilder("123").append("4");//实际创建了一个对象.因此执行速度上也比String快很多.<br/>
    &nbsp;StringBuilder和StringBuffer的区别在于前者是线程不安全的,执行速度快,而后者是线程安全的,比前者慢.<br/>
    &nbsp;因此,在操作少量的数据时用String,单线程并且大数据量时用StringBuilder,多线程并且大数据量时用StringBuffer.<br/>
  2.  HashMap、Hashtable区别.<br/>
    &nbsp;Hashtable线程安全、key和value不允许空、直接用key的hashcode、继承自Dictionary.<br/>
    &nbsp;HashMap线程不安全因此执行效率高些、key和value都允许空、重新计算的hashcode、继承自AbstractMap、contains方法去掉改成containsKey和&nbsp;containsValue.<br/>
  3.  wait-notify的正确调用.示例见：http://www.java67.com/2012/12/producer-consumer-problem-with-wait-and-notify-example.html <br/>
    &nbsp;保证在同步块中调用wait()和notify(),如果阻塞,通过循环来测试等待.<br/>
    &nbsp;synchronized(obj){<br/>
      &nbsp;&nbsp;while(<conditions does not hold>){<br/>
      &nbsp;&nbsp;&nbsp;obj.wait();<br/>
      &nbsp;&nbsp;}<br/>
    &nbsp;}<br/>
    &nbsp;synchronized(obj){<br/>
      &nbsp;&nbsp;obj.notifyAll();<br/>
    &nbsp;}<br/>
  4.  如何强化(线程安全的使用单例)Singleton.<br/>
    &nbsp;1) 枚举Enum：<br/>
      &nbsp;&nbsp;public enum Singleton{ <br/>
        &nbsp;&nbsp;&nbsp;INSTANCE;<br/>
        &nbsp;&nbsp;public void methodA(){...}<br/>
      &nbsp;&nbsp;}    <br/>
    &nbsp;2) final静态变量：<br/>
      &nbsp;private Sigleton(){}<br/>
      &nbsp;public static final Singleton INSTANCE = new Singleton();<br/>
      &nbsp;public void methodB(){...}<br/>
    &nbsp;3) 静态方法：<br/>
      &nbsp;private static final Singleton INSTANCE = new Singleton();<br/>
      &nbsp;private Sigleton(){}<br/>
      &nbsp;public static Singleton getInstance(){<br/>
        &nbsp;&nbsp;&nbsp; return INSTANCE;<br/>
      &nbsp;}<br/>
      &nbsp;public void methodC(){...}<br/>
