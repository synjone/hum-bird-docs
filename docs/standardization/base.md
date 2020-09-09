# 新中新内部环境配置

---

如何你用到了公司内部的一些依赖（比如组件库），那你就需要配制如下的 hosts 配制


### 修改 hosts

```txt
10.9.25.43 npm.campus.com
10.9.25.43 bbs.campus.com
10.9.25.43 yapi.campus.com
```

### 蜂鸟使用教程
#### 一、下载安装`vue cli`脚手架
> 详细教程参考`vue cli`官网,官网地址：`https://cli.vuejs.org/zh/guide/installation.html`

#### 二、安装 `element ui `
> 详细教程参考`element ui `官网,官网地址：`https://element.eleme.cn/#/zh-CN/component/installation`

#### 三、安装 蜂鸟表单编辑器

#### 补充说明：`vue`新项目中是没有`lib`这个文件夹的,这个文件需要在此网址下载
网址：` https://worksite.coding.net/s/a43a8a5d-1bdf-41cc-bf26-258097bbec80 `

![image](https://upload-images.jianshu.io/upload_images/9995156-6c5989fe2167127d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


#### 引入 蜂鸟系统
###### 完整引入
``` 
import FormMaking from '~/lib/form-making-advanced'
import '~/lib/form-making-advanced/dist/FormMaking.css'
Vue.use(FormMaking)
```

###### 引入部分组件
```
import {
  GenerateForm,
  MakingForm
} from '~/lib/form-making-advanced'
import '~/lib/form-making-advanced/dist/FormMaking.css'
Vue.component(GenerateForm.name, GenerateForm)
Vue.component(MakingForm.name, MakingForm)
/* 或写为
 * Vue.use(GenerateForm)
 * Vue.use(MakingForm)
 */
```


