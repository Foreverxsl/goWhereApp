<template>
    <!-- ref可以帮我们获取dom -->
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
            <div class="title border-topbottom">当前城市</div>
            <div class="button-list">
                <div class="button-wrapper">
                    <div class="button">{{this.currentCity}}</div>
                </div> 
            </div>
        </div>
        <div class="area">
            <div class="title border-topbottom">热门城市</div>
            <div class="button-list">
                <div @click="handleCityClick(item.name)" class="button-wrapper" v-for="(item,index) in hot" :key="index">
                    <div class="button">{{item.name}}</div>
                </div> 
            </div>
        </div>
        <div class="area" v-for="(item,index) in cities" :key="index" :ref="index" >
            <div class="title border-topbottom">{{index}}</div>
            <div class="item-list">
                <div @click="handleCityClick(inneritem.name)" class="item border-bottom"
                     v-for="(inneritem) in item" :key="inneritem.id">{{inneritem.name}}
                </div>
            </div>
        </div>
        </div>   
    </div>
</template> 

<script> 
import Bscroll from 'better-scroll'
import { mapState,mapMutations } from 'vuex'
export default {
    name: 'CityList',
    props: {
        cities: Object,
        hot: Array,
        letter: String
    },
    computed: {
        ...mapState({
            currentCity: 'city'
        })
    },
    mounted () {
        this.scroll = new Bscroll(this.$refs.wrapper)
    },
    watch: {
        letter() {
            if(this.letter) {
                //console.log(this.$refs)
                const element = this.$refs[this.letter][0]
                //console.log(this.$refs[this.letter])
                //console.log(this.$refs[this.letter][0])
                this.scroll.scrollToElement(element)
            }
            //console.log(this.letter)
        }
    },
    methods: {
        handleCityClick(city) {
            this.changeCity(city)
            this.$router.push('/')
            //console.log(city)
        },
        ...mapMutations(['changeCity'])
    } 
}
</script>
<style lang="scss" scoped>
    .border-topbottom{
        &:before{
            border-color: #ccc;
        }
        &:after{
            border-color: #ccc;
        }
    }
    .border-bottom{
        &:before{
            border-color: #ccc;
        }
    }
    .list{
        overflow: hidden;
        position: absolute;
        top: 1.58rem;
        left: 0;
        right: 0;
        bottom: 0;
        .title{
            line-height: .54rem;
            background: #eee;
            padding-left: .2rem;
            color: #666;
            font-size: .26rem; 
        }
        .button-list{
            overflow: hidden;
            padding: .1rem .6rem .1rem .1rem;
            .button-wrapper{
                float: left;
                width: 33.3%;
                .button{
                    margin: .1rem;
                    padding: .1rem 0;
                    text-align: center;
                    border: .02rem solid #ccc;
                    border-radius: .06rem;
                }
            }
        }
        .item-list{
            .item{
                line-height: .76rem;
                padding-left: .2rem;
            }
        }

    }
    

</style>
