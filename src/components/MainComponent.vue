<template>
  <div class="wrapper">
      <div class="searching__wrapper">
      <SearchingBar 
      :type="'text'"
      :name="'city'"
      v-model= "currentCity"
      />
      <button class="btn" @click="getWeather">Szukaj</button>
      </div>
      <DisplayWeather 
      v-if = "weatherData" 
      :city = "weatherData.name"
      :data = "weatherData.weather[0]"
      :temp = "weatherData.main"
      />
  </div>
</template>

<script>
import axios from 'axios';
import {ref} from 'vue';

import DisplayWeather from './DisplayWeather.vue'
import SearchingBar from './SearchingBar.vue'

export default {
    name: 'MainComponent',
    components: {
        DisplayWeather,
        SearchingBar
    },
    setup(){
        const API = 'https://api.openweathermap.org/data/2.5/weather';

        const currentCity = ref("");
        let weatherData = ref('');

        function getWeather(){
            axios.get(`${API}?q=${currentCity.value}&units=metric&appid=${process.env.VUE_APP_API_key}&lang=pl`)
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
</script >

<style lang="scss">
    .wrapper{
        height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-evenly;
    }
    .searching__wrapper{
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-block: 30px;

        & > .weather__input:focus + .btn, .weather__input:hover + .btn, .weather__input:focus, .weather__input:hover{
            border-bottom: 2px solid #5681a859;
        }
    }
    .btn{
        background-color: white;
        border: none;
        border-bottom: 2px solid #8ecde659;
        color: #8ecde659;
        height: 50px;
        margin-top: 5px;
        cursor: pointer;
        font-weight: 600;
        font-size: 16px;

        &:hover{
            border-bottom: 2px solid #5681a859;
        }
    }
</style>