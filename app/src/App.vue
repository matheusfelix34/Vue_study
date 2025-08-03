<template>

  <TheHeader>
    <template v-slot:title>
      <h1 class="title-home">Titulo do Header</h1>
    </template>

   <p>Receba o conteudo</p>
  </TheHeader> 
  <div v-show="showHeader">{{ nome }}</div>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>


  


</template>

<script setup>

import { onMounted} from 'vue';
// import HelloWorld from './components/HelloWorld.vue';
 import TheHeader from './components/TheHeader.vue';


let showHeader=true;

let teste ='';

onMounted(()=>{
  teste = document.getElementById('header');
  console.log(teste);
});


</script>

<style>
.title-home{
  font-size: 40px;
  color: green;
}
.title{
  font-size: 20px;
  color: blue;

}
.todos-item{
  background-color: #000;
  margin: 3px 6px;
  padding: 3px 6px;
  color: #fff
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px;
}
</style>
