<script setup>
import { ref, computed } from "vue";
  const name = 'Vue 3'
  
  const counter = ref(0)

  const increment = () => counter.value++

  const decrement = () => counter.value--

  const reset = () => counter.value=0

  const classCounter = computed(()=>{
    if(counter.value === 0){
      return 'zero'
    }
    if(counter.value > 0){
      return 'positive'
    }
    if(counter.value < 0){
      return 'negative'
    }
  })

  const favoritos = ref([])

  const add = () => { 
    favoritos.value.push(counter.value)
  }

  const comprueba = computed(() => {

    const number = favoritos.value.find((num) => num === counter.value)
    return number || number === 0

    // if (number === 0) { return true }
    // return number ? true : false
  })

</script>

<template>
  <div class="space-x-1 text-center mt-3 space-y-3">
    <h1 class="text-3xl">Hola {{ name }}</h1>  
    <h2 :class="classCounter" class="text-xl"> {{ counter }}</h2>
    <div class="inline-flex rounded-md shadow-sm" role="group">
      <button @click="increment" class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-s-lg hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700">Increment</button>
      <button @click="decrement" class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border-t border-b border-r border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700">Decrement</button>
      <button @click="reset" class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border-t border-b border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700">Reset</button>
      <button @click="add" :disabled="comprueba" class="px-4 py-2 text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-e-lg hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700 disabled:text-gray-200 disabled:bg-gray-100">Add</button>
    </div>
    <h2 class="pt-2 text-xl">Mis favoritos</h2>
    <div class="flex justify-center rounded-md shadow-sm" role="group">
      <ul class="w-full text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg">
        <li class="w-full px-4 py-2 border-b border-gray-200 rounded-t-lg dark:border-gray-600" v-for="(num,index) in favoritos" :key="index">
            {{ num }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style>
  h1 {
    color: red;
  }
  .positive {
    color: green;
  }
  .negative {
    color: red;
  }
  .zero {
    color: blue;
  }
</style>

