<script setup>
import PricingComponent from './components/PricingComponent.vue'
let postData = JSON.parse(atob(window.asoneData));  
console.log(postData);

</script>

<template>
  <PricingComponent />
</template>