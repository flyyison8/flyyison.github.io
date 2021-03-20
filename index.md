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

