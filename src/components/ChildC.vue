<template>
  <h2>Child Component C</h2>
  <h3>Child Component C username - {{ userName }}</h3>
  <h3>Child Component C composition username - {{ childUserName }}</h3>

  <h3>Child Component C composition Count - {{ childCount }}</h3>
  <h3>Child Component C composition Hero - {{ firstName }} {{ lastName }}</h3>

  <button @click="incrementCount">Increment count from child</button>
</template>

<script>
import { inject, toRefs } from 'vue' // import inject

  export default {
    name: 'ChildC',
    setup() {
     const childUserName = inject('c_userName', 'Default username' ) // 1st arg -the provided label, 2nd - a default value  
     const childCount = inject('c_count', 0)
     const childHero = inject('c_hero',{})
     const incrementCount = inject('incrementCount')
      return { //always update value from the parent not the child
        childUserName,
        childCount,
        ...toRefs(childHero),
        incrementCount
      }
    },
    inject: ['userName'],
  }
</script>

<style scoped>

</style>