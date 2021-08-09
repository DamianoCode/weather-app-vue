<template>
  <div>
      <img v-if="data" :src="' http://openweathermap.org/img/wn/' + data.weather[0].icon + '.png'" alt="weather image">
      {{data}}
  </div>
</template>

<script>
export default {
    name: 'DisplayWeather',
    props: {
      data:{
      }
    },
    setup(){

      return{

      }
    }
}
</script>

<style>

</style>