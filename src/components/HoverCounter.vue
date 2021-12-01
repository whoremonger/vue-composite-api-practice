<template>
  <div>
    <h2 @mouseover="incrementCount">Hovered {{ count }} times</h2>
  </div>
</template>

<script>
//Options API using mixins (using mixins can confuse variable names)
//import CounterMixin from '../mixins/counter'
import useCounter from '../composables/useCounter'

export default {
  name: 'HoverCounter',
  setup() {
    const { count, incrementCount } = useCounter() //destructure the composable

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