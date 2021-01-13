<template>
  <div>
    <tab-bar>
      <tab-bar-item path='/home'>
        <img slot="item-icon" src="@/assets/img/tabbar/maozi1.png" alt="">
        <img slot="item-icon-active" src="@/assets/img/tabbar/maozi2.png" alt="">
        <div slot="item-text">首页</div>
      </tab-bar-item>
      <tab-bar-item path="/profile">
         <img slot="item-icon" src="@/assets/img/tabbar/daiz1.png" alt="">
         <img slot="item-icon-active" src="@/assets/img/tabbar/daiz2.png" alt="">
        <div slot="item-text">分类</div>
      </tab-bar-item>
      <tab-bar-item path="/category">
         <img slot="item-icon" src="@/assets/img/tabbar/qiu1.png" alt="">
         <img slot="item-icon-active" src="@/assets/img/tabbar/qiu2.png" alt="">
        <div slot="item-text">主页</div>
      </tab-bar-item>
      <tab-bar-item path="/bat">
         <img slot="item-icon" src="@/assets/img/tabbar/zuis1.png" alt="">
         <img slot="item-icon-active" src="@/assets/img/tabbar/zuis2.png" alt="">
        <div slot="item-text">我的</div>
      </tab-bar-item>
    </tab-bar> 
  </div>
</template>

<script>

import TabBar from '../../common/tabber/TabBar.vue'
import TabBarItem from '../../common/tabber/TabBarItem.vue'
export default {
  name:'MyTarBar',
  components: { TabBar,TabBarItem },
}
</script>

<style>

</style>