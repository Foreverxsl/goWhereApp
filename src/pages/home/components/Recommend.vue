<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul>
        <!-- tag=li替换为li标签 -->
        <router-link tag="li" :to="'/detail/' + item.id"
            class="item border-bottom" v-for="item in recommendlist" :key="item.id">
            <div class="item-img-wrapper">
                <img class="item-img" :src="item.imgUrl" />
            </div> 
            <div class="item-info">
                <p class="item-title">{{item.title}}</p>
                <p class="item-desc">{{item.desc}}</p>
                <button class="item-button">查看详情</button>
            </div>
        </router-link>
    </ul>
  </div>
</template>
<script>
export default {
    name:'HomeRecommend',
    props: {
        recommendlist: Array
    },
    data () {
        return {
            /*recommendList : [{
                id: '0001',
                title: '长隆野生动物世界',
                imgUrl: 'https://imgs.qunarzz.com/sight/p0/1811/d4/d4a663613604238ea3.img.jpg_200x200_b412a8a2.jpg',
                desc: '野生动物世界考拉园：“欢欢”和“乐乐”，还有“四代同堂”的考拉大家族，将给游客带来更多欢乐！长隆大熊猫中心：长隆野生动物世界的心脏位置。在2013年7月31日出生的，广东首只大熊猫宝宝以及2014年7月29，都在这里生活。金蛇秘境：全世界知名的20多个蛇精英种族，全都聚会于此，“金蛇秘境”结合原生态蛇生活环境，为游客创造与蛇近距离接触的条件，体验蛇界的缤纷斑斓和灵气，发现它们亲和、美丽、祥瑞的一面。'
            },{
                id: '0002',
                title: '长隆欢乐世界',
                imgUrl: 'https://imgs.qunarzz.com/sight/p0/1811/48/481345746fe3ce9fa3.img.jpg_200x200_fbd18714.jpg',
                desc: '野生动物世界考拉园：“欢欢”和“乐乐”，还有“四代同堂”的考拉大家族，将给游客带来更多欢乐！长隆大熊猫中心：长隆野生动物世界的心脏位置。在2013年7月31日出生的，广东首只大熊猫宝宝以及2014年7月29，都在这里生活。金蛇秘境：全世界知名的20多个蛇精英种族，全都聚会于此，“金蛇秘境”结合原生态蛇生活环境，为游客创造与蛇近距离接触的条件，体验蛇界的缤纷斑斓和灵气，发现它们亲和、美丽、祥瑞的一面。'
            },{
                id: '0003',
                title: '碧水湾温泉度假村',
                imgUrl: 'https://imgs.qunarzz.com/sight/p0/1410/20/41d723daadc98045fe6b7283ba0af40c.jpg_200x200_5a05d5bc.jpg',
                desc: '野生动物世界考拉园：“欢欢”和“乐乐”，还有“四代同堂”的考拉大家族，将给游客带来更多欢乐！长隆大熊猫中心：长隆野生动物世界的心脏位置。在2013年7月31日出生的，广东首只大熊猫宝宝以及2014年7月29，都在这里生活。金蛇秘境：全世界知名的20多个蛇精英种族，全都聚会于此，“金蛇秘境”结合原生态蛇生活环境，为游客创造与蛇近距离接触的条件，体验蛇界的缤纷斑斓和灵气，发现它们亲和、美丽、祥瑞的一面。'
            },{
                id: '0004',
                title: '南沙百万葵园',
                imgUrl: 'https://imgs.qunarzz.com/sight/p0/1603/3c/3c514c20a740128b90.water.jpg_200x200_c7102a23.jpg',
                desc: '野生动物世界考拉园：“欢欢”和“乐乐”，还有“四代同堂”的考拉大家族，将给游客带来更多欢乐！长隆大熊猫中心：长隆野生动物世界的心脏位置。在2013年7月31日出生的，广东首只大熊猫宝宝以及2014年7月29，都在这里生活。金蛇秘境：全世界知名的20多个蛇精英种族，全都聚会于此，“金蛇秘境”结合原生态蛇生活环境，为游客创造与蛇近距离接触的条件，体验蛇界的缤纷斑斓和灵气，发现它们亲和、美丽、祥瑞的一面。'
            },]*/
        }
    }
    
} 
</script>
<style lang="scss" scoped>
.ellipsis{
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
.recommend-title{
    line-height: .8rem;
    background: #eee;
    text-indent: .2rem;
}
.item{
    overflow: hidden;
    display: flex;
    height: 1.9rem;
    .item-img{
        width: 1.7rem;
        height: 1.7rem;
        padding: .1rem;
    }
    .item-info{
        flex: 1;
        padding: .1rem;
        min-width: 0;
    }
    .item-title{
        line-height: .54rem;
        font-size: .32rem;
        @extend .ellipsis;
    }
    .item-desc{
        line-height: .4rem;
        color: #ccc;
        @extend .ellipsis;
    }
    .item-button{
        margin-top: .16rem;
        line-height: .44rem;
        background: #ff9300;
        padding: 0 .2rem;
        border-radius: .06rem;
        color: #fff;
    }

}

</style>
