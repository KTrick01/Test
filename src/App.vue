<script setup>
import { computed } from '@vue/reactivity';
import {ref} from 'vue'
const counter = ref(0);
let color = ref(1)
let array = ref([])

let Disabled = ref("true");

function plus(e, i) {

 
  counter.value ++;
  e()
  
  console.log(counter.value)
}
function minus(e, i) {
  counter.value --;
  e()
  
  console.log(counter.value)
}
function reset(e, i) {
  counter.value = 0;
  e()
  
  
}
function favorite() {
  array.value.push(counter.value)
  
}

const DisableBtn = computed( function () {
  return array.value.includes(counter.value) 
  
})
function colorFun() {
  
  if (counter.value < 0) {
    color.value = "color:red";
    
  } else if (counter.value > 0) {
    color.value = "color: green";
  } else {
    color.value = "color: black"
  }
  
}



</script>
<template>
  <h1 :style="color">{{counter}}</h1>
  <button  @click=plus(colorFun)>Mas</button>
  <button  @click=minus(colorFun)>Menos</button>
  <button  @click=reset(colorFun)>Reset</button>
  <button :disabled="DisableBtn"  @click=favorite >Add</button>
  
  <ul>
    <li v-for="(fav, index) in array" :key="index">
    {{fav}}
    </li>
  </ul>
</template>

<style>
</style> 