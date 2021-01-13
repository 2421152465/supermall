<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends"/>
    <feature-view/>
    <tab-control :titles="['流行','精选','新款']"
    @tabClick='tabClick'/>
    <goods-list :goods="showGoods"/>
   
  </div>
</template>

<script>
import HomeSwiper from './childComps/HomeSwiper'
import RecommendView from './childComps/RecommendView'
import FeatureView from './childComps/FeatureView'

import NavBar from '@/components/common/navbar/NavBar.vue'
import TabControl from '@/components/content/tabControl/TabControl.vue'
import GoodsList from '@/components/content/goods/GoodsList'

import {getHomeMultidata,getHomeGoods} from '@/network/home'

export default {
  name:'home',
  components:{
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabControl,
    GoodsList
  },
  data(){
    return{
      banners:[],
      recommends:[],
      title:['流行','精选','新款'],
      goods:{
        'pop':{pape:0,list:[]},
        'new':{pape:0,list:[]},
        'sell':{pape:0,list:[]},
      },
      currentType:'pop'
    }
  },
  computed:{
    showGoods(){
      return this.goods[this.currentType].list
    }
  },
  created(){
   this.getHomeMultidata()

   this.getHomeGoods('pop')
   this.getHomeGoods('new')
   this.getHomeGoods('sell')
  },
  methods:{
    tabClick(index){
      switch(index){
        case 0:
          this.currentType='pop'
          break
        case 1:
          this.currentType='new'
          break
        case 2:
          this.currentType='sell'
          break
      }
    },
    // 网络请求相关的方法
    getHomeMultidata(){
      getHomeMultidata().then(res =>{
        this.banners = res.data.data.banner.list;
        this.recommends = res.data.data.recommend.list;
      })
    },
    getHomeGoods(type){

      const page = this.goods[type].page + 1
      getHomeGoods(type,page).then(res =>{
        this.goods[type].list.push(...res.data.data.list)
        this.goods[type].page +=1 
      })
    }
  }
}
</script>

<style scoped>
  #home{
    padding-top: 44px;
    padding-bottom: 49px;
  }
  .home-nav{
    background-color: var(--color-text);
    color: white;
    font-weight:bold;
    position: fixed;
    top: 0;
    right: 0;
    left: 0;
    z-index: 9;
  }

  .tab-control{
    position: sticky;
    top: 44px;
    z-index: 9;
  }
</style>