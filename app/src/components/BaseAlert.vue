<template>
    <div :class="baseClass">
        <slot/>
    </div>
</template>

<script setup>

import { computed, defineProps } from 'vue';

// const props= defineProps(['variant'])
const  props = defineProps({ 
    variant:  {
      type: String,
      default: 'success'
    }
    
})


const baseClass = computed(() => {
    return [
        'alert',
        'alert-' + props.variant ? 'alert-' + props.variant : ''
        
    ]
});

</script>

<style scoped>
.alert {
    background-color: dimgray;
   
    padding: 15px;
    border-radius: 5px;
    margin: 10px 0;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.alert-success {
    background-color: #dff0d8;
    color: #3c763d;
}

.alert-error {
    background-color: #f2dede;
    color: #a94442;
}
</style>