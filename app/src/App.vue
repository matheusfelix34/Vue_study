<template>

  <!-- <TheHeader v-show="showHeader"/>
  <div v-show="showHeader">{{ nome }}</div>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <div>

           <h1 :class="{'title': false, 'title-home' : isHome }">
              Curso Vue 3 bolado.
           </h1>

            <div v-for="(obj, index) in todos" :key="obj.id" class="todos-item">
                 {{ index }} - {{ obj.title }} 
                 <img v-if="obj.imageSrc"
                    :src="obj.imageSrc"
                    :alt="obj.imgAlt"
                 >
             </div>
  </div>   

  


</template>

<script setup>
// import HelloWorld from './components/HelloWorld.vue';
// import TheHeader from './components/TheHeader.vue';
  
// let showHeader=false;
// let nome ="Rodolfo";
// let title="title";
let isHome = true;
let todos= [
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
    "completed": false
  }
];
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
