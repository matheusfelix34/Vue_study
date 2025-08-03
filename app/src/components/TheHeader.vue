<template>
    <div id="header" class="header">
        Header
       <slot name="title"/>
     
       <slot />
    </div>
</template>


<script setup>
    
</script>

<style>
    .header {
       background: #000;
       color: #fff; 
    }
</style>