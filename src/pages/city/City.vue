<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities" :hot="hotcities" :letter="letter"></city-list>
        <city-alphabet :cities="cities" @change="handleLetterChange"></city-alphabet>
    </div>
</template> 

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
export default {
    name: 'City',
    data () {
        return {
            cities: {},
            hotcities: [],
            letter: ''
        }
    },
    components: { 
        CityHeader,
        CitySearch,
        CityList,
        CityAlphabet
    },
    methods: {
        getCityInfo() {
            axios.get('/static/mock/city.json').then(this.GetCityInfoSucc)
        },
        GetCityInfoSucc(res) {
            res = res.data;
            if(res.ret && res.data) {
                const data = res.data;
                this.cities = data.cities;
                this.hotcities = data.hotCities;
                //console.log(this.hotcities);
            }
        },
        //父组件监听Alphabet.vue子组件事件
        handleLetterChange(letter) {
            this.letter = letter;
            console.log(letter);

        }
    },
    mounted() {
        this.getCityInfo();
    },

    
}
</script>
<style lang="scss" scoped>

</style>
