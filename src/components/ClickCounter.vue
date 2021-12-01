<template>
  <div>
    <button @click="incrementCount">Clicked {{ count }} times</button>
  </div>
</template>

<script>
//Options API using mixins. Using mixins can confuse variable names. Replace 'mixins' folder with 'composables' folder
//import CounterMixin from '../mixins/counter'
import useCounter from '../composables/useCounter'
export default {
  name: 'ClickCounter',
  setup() {
    const { count, incrementCount } = useCounter(100, 10) //destructure the composable

    return {
      count,
      incrementCount,
      
    }
  }
  //mixins: [CounterMixin],
  
}
</script>

<style scoped>

</style>