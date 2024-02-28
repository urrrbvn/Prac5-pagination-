<script setup>
  import { onMounted, reactive, ref, toRefs } from 'vue';
  import Navigation from './components/Navigation.vue';
  import CardList from './components/CardList.vue';
  import axios from 'axios'

  let recipes = ref([1,2,3])

  let currentSlice = ref([1,2,3,4,5])


  onMounted(async ()=>{
    try{
      const res = await axios.get('https://dummyjson.com/recipes')

      recipes.value = [...res.data.recipes]

      createSlice(1, 1)


    }catch(error){
      console.log('Ошибка', error)
    }
  })

  function createSlice(previous, current){
    if(previous < current){
        if(current !== 1){
        currentSlice.value = [...recipes.value.slice((previous * 6),(current*6))]
        console.log(previous, current)
      }else{
        currentSlice.value = [...recipes.value.slice(0,6)]
      }
    }else{
      if(current !== 1){
      currentSlice.value = [...recipes.value.slice(((current-1)*6),(previous * 6))]
      console.log(previous, current)
    }else{
      currentSlice.value = [...recipes.value.slice(0,6)]
    }
    }
  }

</script>

<template>
  <div class="appContainer" >
    <h1>Recipes</h1>
    <Navigation :createSlice="createSlice" ></Navigation>
    <CardList :currentSlice="currentSlice"></CardList>
  </div>
</template>

<style scoped>

  h1{
    font-size: 48px;
    line-height: 58px;
    margin-bottom: 52px;

    font-weight: 400;
  }
  .appContainer{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>