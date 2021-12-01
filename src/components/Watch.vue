<template>
  <div>
    <!--Options API -->
    <input type="text" placeholder="Name" v-model="name" />

    <!--Composition API -->
    <input type="text" placeholder="First Name" v-model="firstName" />
    <input type="text" placeholder="Last Name" v-model="lastName" />

    <input type="text" placeholder="Reactive First Name" v-model="fName" />
    <input type="text" placeholder="Reactive Last Name" v-model="lName" />

    <input type="text" placeholder="Reactive Hero Name" v-model="options.heroName" />
  </div>
</template>

<script>
import { ref, watch, reactive, toRefs } from 'vue' //add watch function
import _ from 'lodash'

export default {
  name: 'Watch',
  setup() {
    const firstName = ref('')
    const lastName = ref('Fuck')
    const state = reactive({
      fName: '',
      lName: '',
      options:  {
        heroName: ''
      }
    })

   // watch(
      //() => {
      //  return {...state} //make a copy of state
      //}, 
     // function(newValue, oldValue) {
      //console.log('fName Old value', oldValue.fName) //reactive old and new values will be the same
      //console.log('fName New value', oldValue.fName)
      //console.log('lName Old value', oldValue.lName)
     // console.log('lName New value', oldValue.lName)
    //}),

    watch(
      () => _.cloneDeep(state.options),  //use lodash/_.cloneDeep to clone/copy a deep object to have the different old/new 
      //values working again
      function(newValue, oldValue) {
      console.log('fName Old value', oldValue) //watching individual properties - fName
      console.log('fName New value', newValue) //to make deep copy of object use lodash
    },
    {
      deep: true, // to search into a object in a object
    })
  //watch function can accept accepts to use the same function for a different situation. 
  //It can watch multiple sources at the same time. Use array.
    watch([firstName, lastName], (newValues, oldValues) => {
      console.log('Firstname Old Value ', oldValues[0])
      console.log('Firstname New Value ', newValues[0])
      console.log('Lastname Old Value ', oldValues[1])
      console.log('Lastname New Value ', newValues[1])
    }), {
      immediate: true, // executes watcher immediately on page load
    }
      
    return {
      firstName,
      lastName,
      ...toRefs(state)
    }
  },
  data() {
    return {
      name: '',
    }
  },
  watch: {
    name(newValue, oldValue) {
      console.log('Old Value', oldValue)
      console.log('New Value', newValue)
    },

  },
}
</script>

<style scoped>

</style>