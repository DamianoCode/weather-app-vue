<template>
  <div class="container">
      <h2 class="weather__city">{{city}}</h2>
      <div style="width:100%;">
        <img class="icon" v-if="data" :src="' http://openweathermap.org/img/wn/' + data.icon + '@2x.png'" alt="weather image">
        <p class="weather__desc">{{data.description}}</p>
      </div>
      <p class="weather__temp">{{temp.temp}} &#8451;</p>
  </div>
</template>

<script>
export default {
    name: 'DisplayWeather',
    props: {
      data:{
      },
      temp:{

      },
      city:{

      }
    },
    setup(){

      return{

      }
    }
}
</script>

<style lang="scss"  scoped>
  .container{
    font-family: 'Georama', sans-serif;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    width: 500px;
    height: 700px;
    text-align: center;

    background-color: #8ecde659;
    border-radius: 2em;

    & .icon{
      height: 150px;
    }

    & > .weather__city{
      font-size: 30px;
    }

    & > .weather__temp{
      font-size: 50px;
      font-weight: 600;
    }

    & > .weather__desc{
      font-size: 20px;
    }
  }
</style>