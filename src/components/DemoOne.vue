<template>
  <div>
    <h2>{{ name }}</h2>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  name: 'DemoOne',
  setup() {
    const name = ref('Black Nigger')

    setTimeout(() => {  //wont update the DOM but will log it to console. //this is the reactivity of the function
    //Vue doesnt know how the value changes without ref or reactive. Use ref and name.value and declare as const
      name.value = 'White Power'
      console.log(name) 
    }, 2000)

    return {
      name,
    }
  },
}
</script>

<style scoped>

</style>