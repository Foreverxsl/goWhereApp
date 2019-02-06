<template>
  <div>
    <home-header ></home-header>
    <home-swiper :swiper="swiper"></home-swiper>
    <home-icons :iconlist="iconlist"></home-icons>
    <home-recommend :recommendlist="recommendlist"></home-recommend>
    <home-weekend :weekendlist="weekendlist"></home-weekend>
  </div>
</template>
<script>
import { mapState } from 'vuex'
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
export default {
    name:'Home',
    components: {
        HomeHeader,
        HomeSwiper,
        HomeIcons,
        HomeRecommend,
        HomeWeekend
    },
    data (){
      return {
        lastcity: '',
        swiper: [],
        iconlist: [],
        recommendlist: [],
        weekendlist: []
      }
    },
    computed: {
      ...mapState(['city'])
    },
    methods: {
      getHomeInfo () {
        axios.get('/static/mock/index.json?city='+this.city).then(this.getHomeInfoSucc)
      },
      getHomeInfoSucc (res) {
        res=res.data;
        if(res.ret && res.data){
          const data = res.data;
          this.swiper = data.swiperList;
          this.iconlist = data.iconList;
          this.recommendlist = data.recommendList;
          this.weekendlist = data.weekendList;
        }
      }
    },
    mounted () {
      this.lastcity = this.city
      this.getHomeInfo()
    },
    // 只有页面城市修改才重新加载ajax请求
    activated () {
      if(this.lastcity !== this.city) {
        this.lastcity = this.city
        this.getHomeInfo()
      }
    }
} 
</script>
<style lang="scss" scoped>

</style>
