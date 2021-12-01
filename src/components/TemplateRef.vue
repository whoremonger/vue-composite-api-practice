<template>
  <div>
    <!--Options API -->
    <input type="text" ref="inputRef" />
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  name: 'TemplateRef',
  setup () {
    const inputRef = ref(null) //refers to ref attribute in template

    onMounted(() => {  //accepts function as argument
      inputRef.value.focus() //remember to always use .value when accessing the value
    }) 

    return {
      inputRef,
    }
  },
  //Options API
  //mounted() {
    //this.$refs.inputRef.focus()
  //},
}
</script>

<style scoped>

</style>