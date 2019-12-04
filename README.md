# my-test-toast
使用网上的例子，自己测试搭建使用npm发布的内容，并且使用步骤，
具体参考[来源](https://www.jianshu.com/p/62c199d306e1)

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

# 构建npm包并且上传到npm
npm run publish

# 使用插件
## 下载依赖
npm i vue-plugin-my-test-toast --save-dev
## 使用
import Vue from 'vue'
import MyTestToast from 'vue-plugin-my-test-toast'

Vue.use(MyTestToast)

## 在对应的vue实例中就可以this.$toast(msg, options)
例如：
```vue
<template>
  <div>
    <button @click="showToast('top')">TOP</button>
    <button @click="showToast('middle')">MIDDLE</button>
    <button @click="showToast('bottom')">BOTTOM</button>
  </div>
</template>

<script type="text/ecmascript-6">
  import Vue from 'vue'
  import Toast from '@/plugin'
  Vue.use(Toast)
  export default {
    components: {},
    data() {
      return {}
    },
    filters: {},
    mounted: function () {
      this.$nextTick(function () {
      })
    },
    methods: {
      showToast(pos) {
        this.$toast(`您的余额为<span style="color: red;"> ${parseInt(Math.random() * 100)}</span>. 需要充值`, {
          enableHtml: true, // 是否开启内嵌html元素
          autoClose: false, // 是否自动关闭
          position: pos || 'top', // 展示位置
          closeButton: {  // 关闭按钮配置
            text: '充值',
            callback: (toast) => {
              toast.log() // 关闭后触发 toast 中的方法
            }
          }
        })
      }
    },
    watch: {},
    computed: {}
  }
</script>

<style lang="scss" scoped>
</style>

```

## this.$toast(msg, options)的第二个参数说明
- autoClose: [Boolean, Number]: 是否自动关闭,默认值5(即显示后5s关闭)  false: 不自动关闭， 如果是数字(大于0)：就是等待对应的秒(s)后关闭
- closeButton: Object: 关闭按钮的文字和关闭时候的回调函数，默认值: {text: "关闭",callback: undefined}
- enableHtml: Boolean: 是否msg中可以使用html的解析，如果true可以支持html的方式，否则html的文字会按照输入的信息展示
- position: String: 取值范围["top", "middle", "bottom"],规定在垂直方向的三种对齐方式 顶部 、中部 、底部
