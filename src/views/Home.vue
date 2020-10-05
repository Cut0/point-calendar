<template lang="pug">
#app
  point-calendar(
    :month="state.date"
    :cells="state.cells"
  )
</template>
<script>
import { reactive, defineComponent } from '@vue/composition-api'
import moment from 'moment'
import PointCalendar from '@/components/PointCalendar.vue'
export default defineComponent({
  components: { PointCalendar },
  setup() {
    const date = moment(Date.now()).toDate()
    const cells = [
      { day: 1, badges: [{ color: 'blue', value: 12 }] },
      { day: 2, badges: [{ color: 'blue', value: 12 }] }
    ]
    const state = reactive({ date, cells })
    console.log(state)
    return { state }
  }
})
</script>
