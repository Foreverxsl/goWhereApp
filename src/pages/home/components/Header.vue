<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont back-icon">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市/景点/游玩主题
        </div> 
        <router-link to="/city">
            <div class="header-right">{{this.doubleCity}}<span class="iconfont arrow-icon">&#xe64a;</span></div>
        </router-link>
        
    </div>
</template>
<script>
import { mapState,mapGetters } from 'vuex'
export default {
    name:'HomeHeader',
    computed: {
        //...mapState(['city']),
        ...mapGetters(['doubleCity'])
    }
} 
</script>
<style lang="scss" scoped>
    $blue: #00bcd4;
    .header{
        display: flex;
        line-height: .86rem;
        background: $blue;
        color: #fff;
        .header-left{
            float: left;
            width: .64rem;
            .back-icon{
                text-align: center;
                font-size: .4rem;
            }
        }
        .header-input{
            flex: 1;
            height: .64rem;
            line-height: .64rem;
            margin-top: .12rem;
            margin-left: .2rem;
            padding-left: .24rem;
            background: #fff;
            color: #ccc;
            border-radius: .1rem;
            text-align: left;
        }
        .header-right{
            float: right;
            min-width: 1.04rem;
            padding: 0 .1rem;
            text-align: center;
            color: #fff;
            .arrow-icon{
                font-size: .24rem;
                margin-left: .08rem;
            }
        }
        
    }
</style>
