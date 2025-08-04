<template>


  <div>
    <div class="card">
s
    </div>
      <BaseCard/>
  </div>


</template>

<script setup>

import { onMounted} from 'vue';
import BaseCard from '@/components/BaseCard.vue';

 




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
