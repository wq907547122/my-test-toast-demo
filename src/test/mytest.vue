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
