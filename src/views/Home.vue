<template lang="pug">
v-container
  span テスト
  v-row(no-gutters)
    v-col(v-for="(dayName,index) in ['sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat']")
      span {{dayName}}
  v-row(no-gutters v-for="n in weakCount")
    v-col(v-for="(dayData,index) in days.slice((n-1)*7,n*7)")
      calendar-cell(:day="dayData.day")
</template>
<script lang="ts">
import { reactive, defineComponent } from '@vue/composition-api'
import CalendarCell from '../components/CalendarCell.vue'
import moment from 'moment'

function getDaysArray(year: number, month: number) {
  const names = ['sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat']
  const date = new Date(year, month - 1, 1)
  const result = []
  for (let i = 0; i < date.getDay(); i++)
    result.push({ day: '', dayOfTheWeek: names[date.getDay()] })
  while (date.getMonth() == month - 1) {
    result.push({ day: date.getDate(), dayOfTheWeek: names[date.getDay()] })
    date.setDate(date.getDate() + 1)
  }
  for (let i = date.getDay(); i < 7; i++)
    result.push({ day: '', dayOfTheWeek: names[date.getDay()] })
  return result
}

export default defineComponent({
  components: { CalendarCell },
  props: {
    month: {
      type: Object as () => Date,
      require: true,
      default: moment(Date.now()).toDate()
    }
  },
  setup(props) {
    const days = getDaysArray(
      props.month.getFullYear(),
      props.month.getMonth() + 1
    )
    return reactive({ days, weakCount: Math.ceil(days.length / 7) + 1 })
  }
})
</script>
