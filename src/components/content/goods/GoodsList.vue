<template>
  <div class="goods">
    <goods-list-item :goodsItem="item" v-for="(item) in goods" :key="item.iid"/>
  </div>
</template>

<script>
import GoodsListItem from './GoodsListItem'

export default {
  name: 'GoodsList',
  components: {
    GoodsListItem
  },
  props: {
    goods: {
      type: Array,
      default() {
        return []
      } 
    }
  }
}
</script>

<style scoped>
  .goods{
    width: 100%;
    padding: 5px;
    font-size: 13px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }
</style>