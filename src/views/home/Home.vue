<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banner="banner"></home-swiper>
    <recommend-view :recommend="recommend"></recommend-view>
  </div>
</template>

<script>
  import NavBar from 'components/common/navbar/NavBar'
  import HomeSwiper from './childrenComps/HomeSwiper'
  import RecommendView from './childrenComps/RecommendView'

  import { getHomeMultidata } from 'network/home'
  
  export default {
    name: 'Home',
    components: {
      NavBar,
      HomeSwiper,
      RecommendView
    },
    data() {
      return {
        banner: [],
        recommend: [],
        dkeyword: [],
        keywords: []
      }
    },
    created() {
      // 1.请求多个数据
      getHomeMultidata().then(res => {
        console.log(res)
        this.banner = res.data.banner.list
        this.recommend = res.data.recommend.list
        this.dkeyword = res.data.dKeyword.list
        this.keywords = res.data.keywords.list
      })
    },
  }
</script>

<style scoped>
  .home-nav {
    background-color: var(--color-tint);
    color: #fff;
  }
</style>