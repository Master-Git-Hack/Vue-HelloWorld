<script setup>
import { ref } from 'vue'
//para hacer el componente reactivo se usa ref= useState
const name = "Vue 3"
const styleColor = "color:blue"
let counter = 0
const counterRef = ref(0)
const array = [1, 2, 3, 4, 5]
const arrayObj = [
  { id: 1, name: "Vue" },
  { id: 2, name: "React" },
  { id: 3, name: "Angular" },
]

const onClick = () => {
  console.log("Clicked")
  counterRef.value++;
}
const onClickP = (param) => {
  console.log("Clicked", param)
  counter++;
  console.log(counter)
}
</script>
<template>
  <h1>Hello World {{ name }}</h1>
  <br>
  <p v-if="counter%2===0">Odd</p>
  <p v-else>Even</p>
  <p v-bind:style="styleColor">Counter with No Reactivity{{ counter }}</p>
  <p v-bind:style="styleColor">Counter with  Reactivity{{ counterRef }}</p>
  <p :style="styleColor">Hello World {{ name }}</p>
  <br>
  <button @click="onClick">Add with Reactivity</button>
  <button v-on:click="onClickP('some random text')">Add With Param and No Reactivity</button>
  <br>
  <ul>
    <li v-for="item in array" :key="item">{{ item**2 }}</li>
  </ul>
  <br>
  <ol>
    <li v-for="item in arrayObj" :key="item.id">{{ item.name }}</li>
  </ol>
</template>
