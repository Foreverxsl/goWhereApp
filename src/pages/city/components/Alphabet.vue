<template>
    <ul class="list"> 
        <li class="item" :ref="item"
            @click="handleLetterClick"
            @touchstart.prvent="handleTouchStart"
            @touchmove="handleTouchMove"
            @touchend="handleTouchEnd"
            v-for="item in letters" :key="item">{{item}}
        </li>
    </ul>
</template> 

<script> 
export default {
    name: 'CityAlphabet',
    props: {
        cities: Object
    },
    data() {
        return {
            touchStatus: false,
            startY: 0,
            timer: null
        }
    },
    //父组件cities改变触发updated
    updated () {
        this.startY = this.$refs['A'][0].offsetTop
        console.log(this.startY)
    },
    computed: {
        letters() {
            const letters = []
            for(let i in this.cities) {
                letters.push(i)
            }
            return letters
        }
    },
    methods: {
        //兄弟组件传值(先子传父)
        handleLetterClick(e) {
            this.$emit('change',e.target.innerText)
            //console.log(e.target.innerText)
        },
        handleTouchStart() {
            this.touchStatus = true

        },
        //性能低，因为startY是固定的，但是每次滑动执行该方法都会运算一次startY
        handleTouchMove(e) {
            if(this.touchStatus) {
                //const startY = this.$refs['A'][0].offsetTop
                if(this.timer) {
                    /*console.log(this.timer)*/
                    clearTimeout(this.timer)
                }
                // 函数节流（节约该函数执行频率，提高性能）
                this.timer = setTimeout(() => {
                    const touchY = e.touches[0].clientY - 79
                    //除每个字母高度
                    const index = Math.floor((touchY - this.startY) / 20)
                    if(index >=0 && index < this.letters.length){
                        //console.log(index)
                        this.$emit('change',this.letters[index])
                    }
                },16)
                //延迟16ms执行，在16ms内再次执行该操作，会清除上次操作，重新执行本次操作
            }

        },
        handleTouchEnd() {
            this.touchStatus = false
        }
        
    }

    
}
</script>
<style lang="scss" scoped>
    .list{
        display: flex;
        flex-direction: column;
        justify-content: center;
        position: absolute;
        top: 1.58rem;
        right: 0;
        bottom: 0;
        width: .4rem;
        .item{
            line-height: .4rem;
            text-align: center;
            color: #00bcd4;
        }

    }

</style>
