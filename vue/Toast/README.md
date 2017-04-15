使用方法：

1.保证组件上级目录中有Order.js
2.父组件引入Order.js
```
import { Order } from './Order.js'
```
3.显示/隐藏Toast框
```
显示:Order.$emit('Toast', '要显示的内容')
```
