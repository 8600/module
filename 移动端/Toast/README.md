使用方法：

1.保证组件上级目录中有Order.js
2.父组件引入Order.js，加载完毕注册事件

```
import Search from './brick/Search'
import { Order } from './Order.js'
export default {
  components: {
    Search
  },
  created () {
    Order.$on('Toast', (message) => {
      this.searchText = message
    })
  },
  data () {
    return {
      searchText:""
    }
  },
}
```
这时父组件中的 searchText 的值会随着输入框内容的改变而改变
