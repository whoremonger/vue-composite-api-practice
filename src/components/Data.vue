<template>
<!--Can use composition API and Options API in the same component -->
  
  <h2>Options - {{ o_firstName }}</h2> <!--Does not need .value in template -->
  <h2>Options - {{ o_firstName }} {{ o_lastName }} a.k.a {{ o_heroName }}</h2>

  <h2>Composition - {{ c_firstName }}</h2>
  <h2>Composition - {{ greet }}</h2>

  <h2>Composition - {{ c_firstName }} {{ c_lastName }} {{ c_heroName }}</h2>
  <h2>Composition - {{ greetHero }}</h2>

  <h2>Composition {{ state.firstName }} {{ state.lastName }} {{ state.heroName }}</h2>
  <h2>Composition {{ reactiveGreetHero }}</h2>
  
</template>

<script>
import { ref, reactive } from 'vue' //import ref and vue stuff. ref replaces data() function

export default {
  name: 'Data',
  setup() { //entry point for composition APIs "setup()"
    const c_firstName = ref('Clark') //"ref" is a different from the component $ref 
    const c_lastName = ref('Kent')
    const c_heroName = ref('Superman')
    
    //c_firstName.value = 'Diana'
    const greet = `Hello, ${c_firstName.value}` //use .value to change value
    const greetHero = `Hello, ${c_firstName.value} ${c_lastName.value} a.k.a ${c_heroName.value}`
    //console.log('c_firstName', c_firstName ) 
  
    const state = reactive ({ //makes it so you don't need to use .value to access it
      firstName: 'Princess',
      lastName: 'Diana',
      heroName: 'Wonder Woman',
    })

    const reactiveGreetHero = `Hello ${state.firstName} ${state.lastName} a.k.a ${state.heroName}`

    const isLoggedIn = ref(false) //cant to that with reactive types because it only accepts objects. 
    //good for grouping like data (like a profile) together in a reactive object
    const isLoggedInReactive = reactive({
      value: false
    })

  //use ref when dealing with primitive types like string, boolean, int, number
  //use reactive when dealing with objects. Can only accept an object
    return {
      c_firstName: c_firstName,
      c_lastName,
      c_heroName,
      greet,
      greetHero,
      state,
      reactiveGreetHero,
      isLoggedIn,
      isLoggedInReactive,
    }
      
  },
  data() {
    return {
      o_firstName: 'Bruce',
      o_lastName: 'Wayne',
      o_heroName: 'Batman',
    }
  },
}
</script>

<style scoped>

</style>