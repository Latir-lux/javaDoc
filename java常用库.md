# JavaSE常用语法和库

## JavaSE常用语法

### 枚举(enumeration，缩写enum)

#### 适用场景

1.值是有限的几个值；2.只读，不需要修改。

#### 两种实现方式：

##### 1.自定义类实现

```java
class Season {//类
	private String name;
	private String desc;//描述
	//定义了四个对象, 固定.
	public static final Season SPRING = new Season("春天", "温暖");
	public static final Season WINTER = new Season("冬天", "寒冷");
	public static final Season AUTUMN = new Season("秋天", "凉爽");
	public static final Season SUMMER = new Season("夏天", "炎热");
    private Season(String name, String desc) {
    this.name = name;
    this.desc = desc;
}
public String getName() {
    return name;
}
public String getDesc() {
    return desc;
}
@Override
public String toString() {
    return "Season{" +
            "name='" + name + '\'' +
            ", desc='" + desc + '\'' +
            '}';
    }
}
```

特点如下：

1) 构造器私有化
2) 本类内部创建一组对象[四个春夏秋冬]
3) 对外暴露对象（通过为对象添加public final static 修饰符）
4) 可以提供get 方法，但是不要提供set

##### 2.enum关键字实现

```java
enum Season {
    //如果使用了enum 来实现枚举类
    //1. 使用关键字enum 替代class
    //2. public static final Season SPRING = new Season("春天", "温暖") 直接使用
    // SPRING("春天", "温暖") 解读常量名(实参列表)
    //3. 如果有多个常量(对象)， 使用,号间隔即可
    //4. 如果使用enum 来实现枚举，要求将定义常量对象，写在前面
    //5. 如果我们使用的是无参构造器，创建常量对象，则可以省略()
    SPRING("春天", "温暖"), WINTER("冬天", "寒冷"), AUTUMN("秋天", "凉爽"),
    SUMMER("夏天", "炎热")/*, What()*/;
    private String name;
    private String desc;//描述
    private Season2() {//无参构造器
    }
    private Season2(String name, String desc) {
        this.name = name;
        this.desc = desc;
	}
    public String getName() {
        return name;
    }
    public String getDesc() {
        return desc;
    }
    @Override
    public String toString() {
        return "Season{" +
                "name='" + name + '\'' +
                ", desc='" + desc + '\'' +
                '}';
    }
}
//调用代码如下：
Season season1 = Season.Spring;
System.out.println(season1);	//会输出Spring，本质是调用父类Enum的toString
```

注意事项如下：

1. 当我们使用enum 关键字开发一个枚举类时，默认会继承Enum 类, 而且是一个final 类[如何证明],老师使用javap 工具来演示
2. 传统的public static final Season2 SPRING = new Season2("春天", "温暖"); 简化成SPRING("春天", "温暖")， 这里必
   须知道，它调用的是哪个构造器.
3. 如果使用无参构造器创建枚举对象，则实参列表和小括号都可以省略
4. 当有多个枚举对象时，使用,间隔，最后有一个分号结尾
5. 枚举对象必须放在枚举类的行首.

**具体内容查看笔记第十一章枚举部分**

## JavaSE常用库

### 集合与数组

常用库中最多的是集合，集合概念是针对数组的不便之处提出的。

数组的缺陷：

1. 长度开始时必须指定，并且指定后不能更改
2. 保存的必须是同一类型的元素
3. 使用数组进行增加/删除元素的代码比较繁琐

集合的特点：

1. 可以**动态保存**任意多个对象
2. 提供了一系列便于操作对象的方法：add、remove、set、get等
3. 使用集合添加/删除元素的代码较简洁

### 集合的分类

java中的集合类很多，主要分为两大类：

#### Collection

![屏幕截图 2025-01-24 204101](./pictures/屏幕截图 2025-01-24 204101.png)

##### 常用方法：

1. add：添加单个元素
2. remove：删除指定元素
3. contains：查找元素是否存在
4. size：获取元素个数
5. isEmpty：判断是否为空
6. clear：清空
7. addAll：添加多个元素
8. containsAll：查找多个元素是否都存在
9. removeAll：删除多个元素

##### Vector:



#### Map

![屏幕截图 2025-01-24 200545](./pictures/屏幕截图 2025-01-24 200545.png)