<template>
  <div>
    <h2>{{firstName}} {{lastName}}</h2>
    <h2>{{fname}} {{lname}}</h2>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'
  export default {
    name: 'DemoTwo',
    setup() {

      const state = reactive({
        firstName: "Whore",
        lastName: 'Faggot',
      })

      setTimeout(() => {  
        state.firstName = 'Clark'
        state.lastName = 'Kent'
        console.log(state) 
        }, 2000)

        return toRefs(state) //preserves reactivity

      //return {
        //firstName: state.firstName, // do this to bind just the variable name but it inserts a bug in the code.
        //state does not know that it has to react to changes in the property value. use toRefs
        //lastName: state.lastName,
      //}
    },
    data() {
      return {
        fname: 'Bruce',
        lname: 'Wayne'
      }
    }
  }
</script>

<style scoped>

</style>