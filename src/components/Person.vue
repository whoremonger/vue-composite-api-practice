<template>
  <div>
    <input type="text" placeholder="First Name" v-model="firstName" />
    <input type="text" placeholder="Last Name" v-model="lastName" />
  </div>
  <PersonGreeting :firstName="firstName" :lastName="lastName" @callHeros="callHeros" />
</template>

<script>
import { ref } from 'vue'
import PersonGreeting from './PersonGreeting.vue'

export default {
  name: 'Person',
  components: {
    PersonGreeting,
  },
  setup() {
    const firstName = ref('')
    const lastName = ref('')

    function callHeros(hero) {
      alert(`Calling ${hero}`)
    }

    return {
      firstName,
      lastName,
      callHeros,
    }
  }, 
}
</script>

<style scoped>

</style>