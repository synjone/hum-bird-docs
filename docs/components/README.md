# 组件
<span id='组件'></span>


<span id='表单设计器'></span>

## 表单设计器 （MakingForm）

<span id='代码演示'></span>

### 代码演示

```
<template>
  <fm-making-form 
    ref="makingform" 
    style="height: 500px;" 
    preview 
    generate-code 
    generate-json
  >
    <template slot="action">
    </template>
  </fm-making-form>
</template>
```
*使用时需要设置设计器的高度，默认情况高度是根据父元素 100% 来渲染*

#### 自定义操作按钮
```
<template>
  <fm-making-form 
    ref="makingform" 
    style="height: 500px;" 
  >
    <template slot="action">
      <!-- 自定义操作区域插槽 -->
      <el-button type="text" icon="el-icon-upload">保存</el-button>
    </template>
  </fm-making-form>
</template>

```

#### 字段配置

```
<template>
  <fm-making-form 
    ref="makingform" 
    style="height: 500px;"
    :basic-fields="['input', 'textarea']"
    :advance-fields="['blank', 'fileupload']"
    :layout-fields="[]"
  >
  </fm-making-form>
</template>

```

#### 获取 json 数据

```
<fm-making-form 
  ref="makingform" 
  style="height: 500px;" 
  preview 
  generate-code 
  generate-json
>
</fm-making-form>

```

```
const json = this.$refs.makingform.getJSON()

```

### API
<span id='API'></span>


#### Props

| 参数 | 说明 | 类型| 默认值 |
| --- | --- | --- | --- |
| preview | 设计器预览操作按钮显示 | Boolean | fasle |
| generate-json | 设计器生成JSON按钮显示 | Boolean | false |
| generate-code | 设计器生成代码按钮显示 | Boolean | false |
| clearable | 设计器清空按钮显示 | Boolean | false |
| upload | 设计器导入JSON按钮显示 | Boolean | false |
| basic-fields | 设计器左侧基础字段配置 | Array | - |
| advance-fields | 设计器左侧高级字段配置 | Array | - |
| layout-fields | 设计器左侧布局字段配置 | Array | - |
| custom-fields | 设计器自定义字段配置 | Array | - |

#### Slots

| name | 说明 |
| --- | --- |
| action | 设计器头部操作按钮自定义区域 |

#### 方法

通过 [ref](https://cn.vuejs.org/v2/api/#ref) 可以获取到 MakingForm 实例并调用实例方法

| 方法名 | 说明 | 参数 |
| --- | --- | --- |
| getJSON | 获取设计器配置的JSON数据 | - |
| getHtml | 获取设计器生成的可以直接使用的HTML代码 | - |
| setJSON | 设置设计器的配置信息 | (value) 通过getJSON方法获取的JSON数据 |
| clear | 清空设计器 | - |
| handleUndo | 撤销 | - |
| handleRedo | 重做 | - |


#### 基础字段

| type | 字段名 |
| --- | --- |
| input | 单行文本 |
| textarea | 多行文本 |
| number | 计数器 |
| radio | 单选框组 |
| checkbox | 多选框组 |
| time | 时间选择器 |
| date | 日期选择器 |
| rate | 评分 |
| color | 颜色选择器 |
| select | 下拉选择框 |
| switch | 开关 |
| slider | 滑块 |
| text | 文字 |
| html | HTML |

#### 高级字段

| type | 字段名 |
| --- | --- |
| blank | 自定义 |
| imgupload | 图片 |
| editor | 编辑器 |
| cascader | 级联选择器 |
| fileupload | 文件 |
| table | 子表单 |

#### 布局字段

| type | 字段名 |
| --- | --- |
| grid | 栅格布局 |
| tabs | 标签页 |
| divider | 分割线 |

<span id='表单生成器'></span>

## 表单生成器 （GenerateForm）

<span id='代码演示2'></span>

### 代码演示

#### 表单生成

直接根据设计器中生成的 `json` 即可渲染出表单，获取表单数据。

```
<template>
  <div>
    <fm-generate-form 
      :data="jsonData" 
      ref="generateForm"
    >
    </fm-generate-form>
    <el-button type="primary" @click="handleSubmit">Submit</el-button>
  </div>
</template>

```

```
export default {
  data () {
    return {
      jsonData: {"list":[{"type":"input","icon":"icon-input","options":{"width":"100%","defaultValue":"","required":false,"dataType":"string","pattern":"","placeholder":"","customClass":"","disabled":false,"labelWidth":100,"isLabelWidth":false,"hidden":false,"dataBind":true,"showPassword":false,"remoteFunc":"func_1575897887618","remoteOption":"option_1575897887618"},"name":"单行文本","key":"1575897887618","model":"input_1575897887618","rules":[{"type":"string","message":"单行文本格式不正确"}]}],"config":{"labelWidth":100,"labelPosition":"right","size":"small","customClass":""}},
    }
  },
  methods: {
    handleSubmit () {
      this.$refs.generateForm.getData().then(data => {
        alert(JSON.stringify(data))
      }).catch(e => {
      })
    }
  }
}

```

#### 加载表单数据

```
<template>
  <div>
    <fm-generate-form 
      :data="jsonData"
      :value="editData" 
      ref="generateForm"
    >
    </fm-generate-form>
  </div>
</template>

```

```
export default {
  data () {
    return {
      jsonData: {"list":[{"type":"input","icon":"icon-input","options":{"width":"100%","defaultValue":"","required":false,"dataType":"string","pattern":"","placeholder":"","customClass":"","disabled":false,"labelWidth":100,"isLabelWidth":false,"hidden":false,"dataBind":true,"showPassword":false,"remoteFunc":"func_1575897887618","remoteOption":"option_1575897887618"},"name":"名称","key":"1575897887618","model":"name","rules":[{"type":"string","message":"名称格式不正确"}]}],"config":{"labelWidth":100,"labelPosition":"right","size":"small","customClass":""}},
      editData: {
        /* 需要加载的表单数据可以在这里进行设置 */
        name: 'Gavin'
      },
    }
  }
}

```

#### 表单字段值改变事件

表单字段值改变后会触发 `on-change` 事件。

```
<template>
  <div>
    <fm-generate-form 
      :data="jsonData" 
      @on-change="onChange"
      :value="formData"
      ref="generateForm"
    >
    </fm-generate-form>
  </div>
</template>

```

```
export default {
  data () {
    return {
      jsonData: {"list":[{"type":"input","icon":"icon-input","options":{"width":"100%","defaultValue":"","required":false,"dataType":"string","pattern":"","placeholder":"","customClass":"","disabled":false,"labelWidth":100,"isLabelWidth":false,"hidden":false,"dataBind":true,"showPassword":false,"remoteFunc":"func_1575897887618","remoteOption":"option_1575897887618"},"name":"名称","key":"1575897887618","model":"name","rules":[{"type":"string","message":"名称格式不正确"}]},{"type":"text","icon":"icon-wenzishezhi-","options":{"defaultValue":"","customClass":"","labelWidth":100,"isLabelWidth":false,"hidden":false,"dataBind":true,"remoteFunc":"func_1575906202073","remoteOption":"option_1575906202073"},"name":"","key":"1575906202073","model":"show","rules":[]}],"config":{"labelWidth":100,"labelPosition":"right","size":"small","customClass":""}},
      formData: {
        show: ''
      }
    }
  },
  methods: {
    onChange (field, value) {
      if (field == 'name') {
        this.formData.show = value
      }
    }
  }
}

```

### API2

#### Props

| 参数 | 说明| 类型 | 默认值 |
| --- | --- | --- | --- |
| data | 表单json配置数据 | Object | - |
| value | 表单数据 | Object | - |
| remote | 表单获取数据远端方法 | Object | {} |
| edit | 表单可编辑状态 | Boolean | true |
| remote-option | 表单动态选项配置 | Object | {} |

#### Events

| 事件名| 说明 | 回调参数 |
| --- | --- | --- |
| on-change | 表单数据变化时触发，在 Antd 表单生成器中废弃使用 | field: 数据改变的字段标识value: 数据改变后的值data: 表单数据 |
| on-${ID}-change | 表单数据变化时触发，ID为配置的字段标识 | value: 数据改变后的值 |

#### 方法

通过 `ref` 可以获取到 GenerateForm 实例并调用实例方法

| 方法名 | 说明 | 参数 |
| --- | --- | --- |
| getData | 获取表单数据 | - |
| reset | 重置表单数据 | - |
| setData | 设置表单数据 | 表单数据，例 {key: value} |
| display | 显示表单隐藏的表单字段 | fields : 字段标识数组，例 ['name'] |
| hide | 隐藏表单字段 | fields : 字段标识数组，例 ['name'] |
| disabled | 动态设置表单禁用字段 | fields : 设置字段标识数组
disabled : 是否禁用 |

## 表单生成器 （GenerateAntdForm）
```
<fm-generate-antd-form></fm-generate-antd-form>
```