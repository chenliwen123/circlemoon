# 业务组件圈阅 circlemoon


## 这是一个Vue2 的组件

> 使用方法如下 <br>
> [使用文件Dome](https://github.com/chenliwen123/circlemoon/blob/main/index.vue)

## prop

| 参数        | 说明    |  类型   |
| -------    | -----  | ---- |
| dom        | 传入的表格(一般是echarts的容器)      |   DOM元素    |
| value / v-model | 是否显示      |   Boolean    |
| imgurl        | 签名图片的路径     |   String    |
————| ———————————————|—————

## Slots 

| name        | 说明    | 
| -------    | -----  | 
| header     | 顶部操作按钮
———————|—————————————————————

```
let newimg = this.$refs.circlemoon.save();
console.log(newing)// 输出的是一个base64的图片地址
```