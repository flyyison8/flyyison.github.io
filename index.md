### 1、只要这个数不是空值才进行下去

```markdown
        
guard let view = view as? UIView else { return }

```

### 2、观察者设计模式，就是属性的值改变了，就发出通知。观察者模式有两种，一个是通知，一个是KVO.
