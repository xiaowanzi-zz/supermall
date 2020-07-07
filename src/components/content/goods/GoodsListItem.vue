<template>
  <div class="goods-item">
    <img :src="goodsItem.show.img" alt="">
    <div class="goods-info">
      <p>{{goodsItem.title}}</p>
      <span class="price">{{goodsItem.price}}</span>
      <span class="collect">{{goodsItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GoodsListItem',
  props: {
    goodsItem: {
      type: Object,
      default() {
        return {}
      }
    }
  }
}
</script>

<style scoped>
  .goods-item {
    width: 49.2%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .goods-item img {
    width: 100%;
    border-radius: 5px;
    /* css3图片缩放 */
    /* object-fit: contain; */
    /* object-fit: cover; */
    /* object-fit: fill; */
  }
  .goods-info{
    padding: 5px 0;
    text-align: center;
  }
  .goods-info p {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .goods-info .price{
    color: var(--color-tint);
  }
  .goods-info .collect {
    padding: 0 20px;
    background: url('~assets/img/common/collect.svg') no-repeat 5px 0;
    background-size: 13px;
  }
</style>
