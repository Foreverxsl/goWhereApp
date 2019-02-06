<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
        <li class="item border-bottom" v-for="item in weekendlist" :key="item.id">
            <div class="item-img-wrapper">
                <img class="item-img" :src="item.imgUrl" />
            </div>
            <div class="item-info">
                <p class="item-title">{{item.title}}</p>
                <p class="item-desc">{{item.desc}}</p>
            </div>
        </li>
    </ul>
  </div>
</template>
<script>
export default {
    name:'HomeRecommend',
    props: {
        weekendlist: Array
    },
    data () {
        return {
            /*weekendList : [{
                id: '0001',
                title: '长隆野生动物世界',
                imgUrl: 'https://imgs.qunarzz.com/sight/source/1811/15/66f14e0fd6fbb.jpg_r_640x214_5d69f21d.jpg',
                desc: '野生动物世界考拉园：“欢欢”和“乐乐”，还有“四代同堂”的考拉大家族，将给游客带来更多欢乐！长隆大熊猫中心：长隆野生动物世界的心脏位置。在2013年7月31日出生的，广东首只大熊猫宝宝以及2014年7月29，都在这里生活。金蛇秘境：全世界知名的20多个蛇精英种族，全都聚会于此，“金蛇秘境”结合原生态蛇生活环境，为游客创造与蛇近距离接触的条件，体验蛇界的缤纷斑斓和灵气，发现它们亲和、美丽、祥瑞的一面。'
            },{
                id: '0002',
                title: '长隆野生动物世界',
                imgUrl: 'https://imgs.qunarzz.com/sight/source/1811/b8/5d599bbdcf8b57.jpg_r_640x214_2ee055e3.jpg',
                desc: '野生动物世界考拉园：“欢欢”和“乐乐”，还有“四代同堂”的考拉大家族，将给游客带来更多欢乐！长隆大熊猫中心：长隆野生动物世界的心脏位置。在2013年7月31日出生的，广东首只大熊猫宝宝以及2014年7月29，都在这里生活。金蛇秘境：全世界知名的20多个蛇精英种族，全都聚会于此，“金蛇秘境”结合原生态蛇生活环境，为游客创造与蛇近距离接触的条件，体验蛇界的缤纷斑斓和灵气，发现它们亲和、美丽、祥瑞的一面。'
            },{
                id: '0003',
                title: '长隆野生动物世界',
                imgUrl: 'https://imgs.qunarzz.com/sight/source/1811/f8/29dfa785277839.jpg_r_640x214_7d051523.jpg',
                desc: '野生动物世界考拉园：“欢欢”和“乐乐”，还有“四代同堂”的考拉大家族，将给游客带来更多欢乐！长隆大熊猫中心：长隆野生动物世界的心脏位置。在2013年7月31日出生的，广东首只大熊猫宝宝以及2014年7月29，都在这里生活。金蛇秘境：全世界知名的20多个蛇精英种族，全都聚会于此，“金蛇秘境”结合原生态蛇生活环境，为游客创造与蛇近距离接触的条件，体验蛇界的缤纷斑斓和灵气，发现它们亲和、美丽、祥瑞的一面。'
            },{
                id: '0004',
                title: '长隆野生动物世界',
                imgUrl: 'https://imgs.qunarzz.com/sight/source/1602/9c/39c5ce9ff58609.jpg_r_640x214_efb90102.jpg',
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
.title{
    line-height: .8rem;
    background: #eee;
    text-indent: .2rem;
}
.item{
    .item-img-wrapper{
        overflow: hidden;
        height: 0;
        padding-bottom: 37.09%; 
        .item-img{
            width: 100%;
        }
    }
    .item-info{
        padding: .1rem;
    }
    .item-title{
        line-height: .54rem;
        font-size: .32rem;
        text-align: left;
        @extend .ellipsis;
    }
    .item-desc{
        line-height: .4rem;
        color: #ccc;
        text-align: left;
        @extend .ellipsis;
    }
}

</style>
