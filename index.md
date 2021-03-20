### 1、只要这个数不是空值才进行下去

```markdown
        
guard let view = view as? UIView else { return }

```

### 2、观察者设计模式，就是属性的值改变了，就发出通知。观察者模式有两种，一个是KVO, KVO可以获取到新旧两个值，一个是通知.
```markdown

import UIKit

class ATKVOModel: NSObject {
   // dynamic需要的加上@objc
   @objc dynamic var name: String = "666"
}

-------------------------------------------------------------------------------------

        observer = model.observe(\ATKVOModel.name, options: [.old, .new]) { (model, change) in
          if let old = change.oldValue {
            print(old) //666
          }
          if let new = change.newValue {
            print(new) // Albert
          }
        }

        // 修改model的值
        model.name = "Albert"
        
```

### 3、struct与class的区别
struct和class是swift的两大数据结构，理解struct和class很重要

1、class是引用类型的数据结构，struct是值类型的数据结构，枚举也是值类型
```markdown

func kk() ->String {
    
    //classtest是定义的一个类
    let class1 = classtest()
    //class是引用类型，那么我将class1赋值给class2时，它们两个是同时引用同一个类，也就是说我在class2上修改类里面a的值，而class1也会跟着改变，因为它们是引用同一个类

    let class2 = class1
    class2.a = 100
    print(class1.a) // 100

}

class classtest {
    var a = 10
    var b = 20
}

```
2、class声明对象时用的是let，但它能够修改class类里面变量的值是因为:let是定义为常量，那么对象对类的引用不可以改变，但还是可以修改类的值的
struct声明对象为var类型，因为struct是值类型，那么对象就类似于一个值，当要改变其内部的值时，var是可行的，let则会报错
如果在struct里面添加方法来修改属性的值，那么要在方法的前面加上mutating，class上不用

```markdown

struct structtest {
    var d = 30
    mutating func a(add:Int) {
        d = d + add
    }
}
```
3、struct是存放在栈空间上的，而class是存放在堆空间上的，因此使用struct的访问速度会更快。
4、类和结构体的第一个区别是类没有逐一成员构造器。这意味着只要你的类里有属性，你就必须自行创建构造器。
```markdown

class Dog {
  var name: String
  var breed: String

  init(name: String, breed: String) {
    self.name = name
    self.breed = breed
  }
}
```
创建类的实例跟创建结构体的实例方式一样：
```markdown
let poppy = Dog(name: "Poppy", breed: "Poodle")
```


