<template>
    <div>
        <router-link to="/" tag="div" v-show="showAbs" class="header-abs">
            <div class="iconfont header-abs-back">&#xe624;</div>
        </router-link>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
             <router-link to="/">
                <div class="iconfont header-fixed-back">&#xe624;</div>
            </router-link>
            景点详情
        </div>

    </div>
</template>

<script>
    export default {
        name: "DetailHeader",
        data() {
            return {
                showAbs: true,
                opacityStyle: {
                    opacity: 0
                }
            }
        },
        methods: {
            handleScroll() {
                //console.log('scroll')
                const top = document.documentElement.scrollTop
                if(top > 60) {
                    let opacity = top / 140
                    opacity = opacity > 1 ? 1 : opacity
                    this.opacityStyle= { opacity }
                    this.showAbs = false
                }else {
                    this.showAbs = true
                }        
            }
        },
        // 在keep-alive组件激活时使用，当页面存在缓存的时候执行该函数,每进页面都会调用
        activated () {
            window.addEventListener('scroll',this.handleScroll)
        },
        // 全局事件解绑
        // keep-alive组件停用时调用,在页面结束时触发该方法，可清除掉滚动方法等缓存。
        deactivated () {
            window.removeEventListener('scroll',this.handleScroll)
        },
       
    
         
    }
</script>

<style lang='scss' scoped>
    .header-abs{
        position: absolute;
        left: .2rem;
        top: .2rem;
        width: .8rem;
        height: .8rem;
        line-height: .8rem;
        border-radius: .4rem;
        text-align: center;
        background: rgba(0,0,0,.8);
        .header-abs-back{
            color: #fff;
            font-size: .4rem;

        }
    }
    .header-fixed{
        z-index: 2;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        height: .86rem;
        line-height: .86rem;
        text-align: center;
        color: #fff;
        background: #00bcd4; 
        font-size: .32rem;
        .header-fixed-back{
            position: absolute;
            top: 0;
            left: 0;
            width: .64rem;
            text-align: center;
            font-size: .4rem;
            color: #fff;
        }
    }
</style>