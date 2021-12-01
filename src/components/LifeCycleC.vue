<template>
  <div>
    <!-- Composition API Lifecycle Hooks -->
    Composition API Lifecycle Hooks
  </div>
</template>

<script>
import {
     onBeforeMount,
     onMounted,
     onBeforeUpdate,
     onUpdated,
     onBeforeUnmount,
     onUnmounted } from 'vue' //the setup() method replaces the first 2 lifecycle hooks beforeCreate() and created()
    //Composition API changes the names and puts "on" in the names
  export default {
    name: 'LifeCycleC',
    setup() {
      onBeforeMount(() => {
        console.log('LifeCycleC onBeforeMount()')
      })
      onMounted(() => {
        console.log('LifeCycleC onMounted()')
      })
      onBeforeUpdate(() => {
        console.log('LifeCycleC onBeforeUpdate()')
      })
       onUpdated(() => {
        console.log('LifeCycleC onUpdated()')
      })
      onBeforeUnmount(() => {
        console.log('LifeCycleC onBeforeUnmount()')
      })
      onUnmounted(() => {
        console.log('LifeCycleC onUnmounted()')
      })
      return {

      }
    }
   
  }
</script>

<style scoped>

</style>