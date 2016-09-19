## Java面试基础（推荐书籍Java Programming Interview Exposed）
  1.  String、StringBuilder、StringBuffer的区别.<br/>
    &nbsp;String:不可变对象,String s = "123";s=s+4;//结果是"1234",实际JVM创建了两个对象,第一个对象被赋值"123",第二个对象执行s+4后第一个对象会被GC.<br/>
    &nbsp;StringBuilder和StringBuffer:对象可变,StringBuiler sb = new StringBuilder("123").append("4");//实际创建了一个对象.因此执行速度上也比String快很多.<br/>
    &nbsp;StringBuilder和StringBuffer的区别在于前者是线程不安全的,执行速度快,而后者是线程安全的,比前者慢.<br/>
    &nbsp;因此,在操作少量的数据时用String,单线程并且大数据量时用StringBuilder,多线程并且大数据量时用StringBuffer.<br/>
  2.  
    
    
