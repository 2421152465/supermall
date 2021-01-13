<template>
  <div class="goods-item">
    <img :src="goodsItem.show.img" alt="">
    <div class="goods-info">
      <p>{{goodsItem.title}}</p>
      <span class="price">￥{{goodsItem.price}}</span>
      <span class="collect">★{{goodsItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    goodsItem:{
      type:Object,
      default(){
        return {}
      }
    }
  }
}
</script>

<style>
.goods-item{
  width: 48%;

}
.goods-item img{
    width: 100%;
    border-radius: 10px ;
}
.goods-info p{
  font-size: 13px;
  overflow: hidden;
  text-overflow:ellipsis;
  white-space: nowrap;
 
}
.goods-info{
  text-align: center;
}
.price{
  font-size: 13px;
  color: red;
  padding-right: 10px;
}
.collect{
  font-size: 14px;
  color: rebeccapurple;
}
</style>