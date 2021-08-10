<template>
      <input 
      class="weather__input"
      :type="type" 
      :name="name"
      :placeholder="placeholder"
      @input="(e) => $emit('update:modelValue', e.target.value)"
      >
</template>

<script>
export default {
    name: 'SearchingBar',
    props:{
        name:{
            type: String,
            required: true,
        },
        type:{
            type: String,
            default: 'text',
        },
        placeholder:{
            type: String,
            default: 'Podaj miasto',
        },
        modelValue:{
            type: String,
        }
    }

}
</script>

<style lang="scss">
    .weather__input{
        width: calc(100% - 30vw);

        border: none;
        border-bottom: 2px solid #8ecde659;
        font-size: 25px;
        height: 50px;
        outline: none;
    }
</style>