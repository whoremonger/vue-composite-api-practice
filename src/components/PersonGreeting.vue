<template>
<!-- Composition and props -->
<!-- Composition and custom events -->
  <div>
    Hello: {{ fullName }} <!-- Best way to combine data is with computed -->
    <button @click="sendEvent">Call Heros</button>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  name: 'PersonGreeting',
  setup(props,context) { //props go inside setup function arguments //add context too for custom events
    console.log(context)
    const fullName = computed(() => {
      return `${props.firstName} ${props.lastName}` //will not work because setup function is called before DOM mounts
    }) //accepts function as argument

    function sendEvent() {
      context.emit('callHeros', fullName.value)
    }

    return {
      fullName,
      sendEvent,
    }
  },
  props: ['firstName', 'lastName'],
  emits: ['callHeros'], //list he custom event in emits array to define it
 ///computed: { //Options API
   /// fullName() {
      //return `${this.firstName} ${this.lastName}` //Use "this"
   // }
  //}
}
</script>

<style scoped>

</style>