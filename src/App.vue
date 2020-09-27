<template lang="pug">
#app
  router-view(
    :month="state.date"
    :cells="state.cells"
  )
</template>
<script lang="ts">
import { reactive, defineComponent } from '@vue/composition-api'
import moment from 'moment'

export default defineComponent({
  setup(props) {
    const date = moment(Date.now()).toDate()
    const cells = [
      { day: 1, badges: [{ color: 'blue', value: 12 }] },
      { day: 2, badges: [{ color: 'blue', value: 12 }] }
    ]
    const state = reactive({ date, cells })
    return { state }
  }
})
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
