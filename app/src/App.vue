<template>

  <!-- <TheHeader v-show="showHeader"/>
  <div v-show="showHeader">{{ nome }}</div>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <div>

           <h1  @:click="receba" :class="{'title': false, 'title-home' : isHome }">
              Vue 3
           </h1>
           <br><br>
           <h1 >
            fullname: {{ fullname }}
           </h1>

            <br><br>
            <h1 >
            Todos Concluidos: {{ todoCompleted.length }}
           </h1>

            <div v-for="(obj) in todoCompleted" :key="obj.id" >
                {{ obj.title }} 
               
             </div>
             <br><br>

             <h1 >
            Todos em aberto: {{ todoUnCompleted.length }}
             </h1>
             
             <div v-for="(obj) in todoUnCompleted" :key="obj.id" >
                {{ obj.title }} 
               
             </div>
             <br><br>
              <h1>
                Todos</h1>
             <div v-for="(obj) in todos" :key="obj.id" >
                <input @:click="status" type="checkbox" v-model="obj.completed"> {{ obj.title }} 
               
             </div>


             <br><br>
             <form action="https://www.google.com/" @submit="onSubmit">
              <input  id="nome" value="">
              <br><br>
              <input id="apelido" value="">
              <br><br>
                <button type="submit">receba</button>
             </form>
  </div>   

  


</template>

<script setup>

import { computed, ref } from 'vue';
// import HelloWorld from './components/HelloWorld.vue';
// import TheHeader from './components/TheHeader.vue';
  
// let showHeader=false;
let first_name ="Rodolfa";
let last_name ="Guanabara";




let isHome = true;
let todos=
ref(
[
  {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false,
    'imageSrc': "https://picsum.photos/200/300",
    'imgAlt'  : 'Foto aleátoria'
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false,
    'imageSrc': "https://picsum.photos/200/300",
    'imgAlt'  : 'Foto aleátoria'
  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": true
  }
]

);

function receba($evt){
  alert($evt);
}

function status(){
  console.log(todos.value)
}

function onSubmit(event){
 
  console.log(event)
  event.preventDefault();
      
}

const fullname  =computed(() => {
  return `${first_name} ${last_name}`;
});

const todoCompleted  =computed(() => {
  return todos.value.filter((todo) => todo.completed);
});

const todoUnCompleted  =computed(() => {
  return todos.value.filter((todo) => !todo.completed);
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
