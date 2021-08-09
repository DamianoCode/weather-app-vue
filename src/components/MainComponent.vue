<template>
  <div>
      <input type="text" v-model="currentCity">
      <button @click="getWeather">Szukaj</button>
      <DisplayWeather :data="weatherData"/>
  </div>
</template>

<script>
import axios from 'axios';
import {ref} from 'vue';

import DisplayWeather from './DisplayWeather.vue'

export default {
    name: 'MainComponent',
    components: {
        DisplayWeather
    },
    setup(){
        const API = 'https://api.openweathermap.org/data/2.5/weather';

        const currentCity = ref("");
        let weatherData = ref('');

        function getWeather(){
            axios.get(`${API}?q=${currentCity.value}&units=metric&appid=${process.env.VUE_APP_API_key}`)
            .then(resp => {
                weatherData.value = resp.data;
            })
            .catch( (e) => console.log(e));
        }
        return{
            getWeather,
            weatherData,
            currentCity
        }
    }
}
</script>

<style>

</style>