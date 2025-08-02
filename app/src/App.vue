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
              
              <br><br>
              <select   v-model="pageCount">
                <option value="1">Opção 1</option>
                <option value="2">Opção 2</option>
                <option value="3">Opção 3</option>
                <option value="4">Opção 4</option>
              </select>
              <br><br>

              <br><br>
              <select  v-model="titulo" id="titulos">
              <option v-for="(title, index) in todoTitles" :key="index" :value="index" >{{ title }}</option>
              </select>
              <br><br>
              <select v-model="chapter" id="chapters">
                <option v-for="(chapter, index) in chapters" :key="index" :value="index" >{{ chapter }}</option>
              </select>

              <br><br>

                <input type="text" v-model="objeto.first_name" placeholder="Digite seu nome">
                <br><br>
                <input type="text" v-model="objeto.last_name" placeholder="Digite seu sobrenome">
                <br><br>

                {{ objeto.first_name }} {{ objeto.last_name }}

            <br><br>
                <button type="submit">receba</button>
             </form>
  </div>   

  


</template>

<script setup>

import { computed, ref, watch } from 'vue';
// import HelloWorld from './components/HelloWorld.vue';
// import TheHeader from './components/TheHeader.vue';
  
// let showHeader=false;
let titulo=  ref('');
let chapter =ref('');
let first_name ="Rodolfa";
let last_name ="Smash";
let name= ref("Thanos Guanabara");
let pageCount = ref(4);

let objeto = ref({
  first_name: "Rodolfa",
  last_name: "Smash"
});

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

let chapters =ref(['Introdução', 'Préfacio', 'Agradecimentos']);

const todoTitles = computed(() =>{
   return todos.value.map((todo) => todo.title )
});
 

const fullname  =computed(() => {
  return `${first_name} ${last_name}`;
});

const todoCompleted  =computed(() => {
  return todos.value.filter((todo) => todo.completed);
});

const todoUnCompleted  =computed(() => {
  return todos.value.filter((todo) => !todo.completed);
});

watch(titulo, (value)=>{
  console.log('Titulo alterado para:' + value);
  atualizarSelect(value);
  chapter.value ='';
});



watch(name, (value) => {
  if(value.length < 3){
    console.log('O nome deve ter mais de 3 caracteres')
    return;
  }
  saveName();
});

watch(pageCount,() => {
  ajaxChangePage();
});

watch(objeto, () => {
  console.log('Objeto alterado');
},
{
  deep: true
});

function atualizarSelect(value){
 
  if(value === 0){
    chapters.value = ['Capitulo 1', 'Capitulo 2', 'Capitulo 3'];
  }
  if(value === 1){
    chapters.value = ['Capitulo 4', 'Capitulo 5', 'Capitulo 6'];
  }

  if(value === 2){
    chapters.value = ['Capitulo 7', 'Capitulo 8', 'Capitulo 9'];
  }
}

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

function saveName(){
  console.log('Ajax para salvar o nome')
  console.log(name.value)
}

function ajaxChangePage(){
  console.log('Paginação alterada para: ' + pageCount.value);
 
}


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
