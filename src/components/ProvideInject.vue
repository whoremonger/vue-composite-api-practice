<template>
    <h3>Parent Component {{ name }}</h3>
    <h3>Parent Component count {{ count }}</h3>
    <h3>Parent Component hero {{ firstName }} {{ lastName }}</h3>

    <button @click="incrementCount">Increment Count</button>

    <ChildA />
</template>

<script>
import ChildA from './ChildA.vue' // import provide
import { provide, ref, reactive, toRefs } from 'vue'

  export default {
    components: {
      ChildA
    },
    name: 'ProvideInject',
    setup() {
      provide('c_userName', 'Fucker') //1st arg - label of value,  actual value you want to provide
      const count  = ref(0)

      function incrementCount() {
        count.value++
      }

      const state = reactive({
        firstName: 'Ass',
        lastName: 'Hole'
      })
      provide('c_count', count)
      provide('c_hero', state)
      provide('incrementCount', incrementCount)

      return {
        count,
        ...toRefs(state),
        incrementCount,
      }
    },
    data() {
      return {
        name: 'Cock Sucker'
      }
    },
    provide() {
      return {
        userName: this.name,
      }
    },
  }
</script>

<style scoped>

</style>