使用教程：

1.保证组件上级目录中有Order.js
2.父组件引入Order.js
```
import { Order } from './Order.js'
```
3.显示/隐藏Loading框
```
显示:Order.$emit('Loading', 'show')
隐藏:Order.$emit('Loading', 'hide')
```
