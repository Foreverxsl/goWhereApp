<template>
    <div class="wrapper">
        <swiper :options="swiperOption" v-if="showSwiper">
        <swiper-slide v-for="item in swiper" :key="item.id">
            <img class="swiper-img" :src="item.imgUrl" />
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>
<script>
export default {
    name: 'HomeSwiper',
    props:{
        swiper: Array
    },
    data () {
        return {
            swiperOption: {
                pagination: '.swiper-pagination',
                loop: true,
            }

        }
    },
    computed: {
        showSwiper() {
            return this.swiper.length;
        }
    }
    
}
</script>
<style lang='scss' scoped>
    .wrapper{
        width: 100%;
        height: 0;
        overflow: hidden;
        padding-bottom: 31.25%;
        background: #eee;
        .swiper-img{
            width: 100%;
            height: 100%;
        }
    }
    .swiper-container-horizontal{
        height: 2.343rem;
    }

</style>
