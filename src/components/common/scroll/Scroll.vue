<template>
  <!-- ref绑定在组件上，通过this.$refs.refname获取的是一个组件对象
    如果绑定的是普通元素，获取的是普通元素
   -->
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
  import BScroll from 'better-scroll'

  export default {
    name: 'Scroll',
    props: {
      probeType: {
        type: Number,
        default: 0
      },
      pullUpLoad: {
        type: Boolean,
        default: false
      }
    },
    data() {
      return {
        scroll: null
      }
    },
    mounted() {
      // 1.创建BScroll对象
      this.scroll = new BScroll(this.$refs.wrapper, {
        click: true,
        probeType: this.probeType,
        pullUpLoad: this.pullUpLoad
      })
      // 2.监听滚动的位置
      this.scroll.on('scroll',(position) => {
        this.$emit('scroll',position)
      })
      // 3.监听上拉事件
      this.scroll.on('pullingUp', () => {
        this.$emit('pullingUp')
      })
    },
    updated() {
      this.scroll.refresh()
    },
    methods: {
      scrollTo(x, y, time=300) {
        this.scroll.scrollTo(x, y, time)
      },
      fiinshPullUp() {
        this.scroll.fiinshPullUp()
      }
    },
  }
</script>

<style scoped>

</style>