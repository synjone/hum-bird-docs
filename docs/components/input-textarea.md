# 多行输入框

使用方式与普通输入框一样,不同点会监听`blur`事件,会进行校验并提示

### Attributes

| 参数        |          说明          |   类型 | 可选值 |       默认值 |
| ----------- | :--------------------: | -----: | -----: | -----------: |
| v-model     |         绑定值         |    any |     -- |           -- |
| content     |          内容          |    any |     -- |           -- |
| placeholder |     输入框占位文本     | string |     -- | 请输入身份证 |
| width       |     输入框宽度(px)     | string |     -- |         100% |
| maxLength   | 原生属性，最大输入长度 | string |     -- |           -- |

>基本上包含了 `elementUI` 属性 ,`api`参考地址: https://element.eleme.cn/#/zh-CN/component/input