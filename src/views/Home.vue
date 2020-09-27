<template lang="pug">
v-container
  span テスト
  v-row(no-gutters)
    v-col(v-for="(dayName,index) in ['sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat']")
      span {{dayName}}
  v-row(no-gutters v-for="n in state.weekCount")
    v-col(v-for="(params,index) in state.cells.slice((n-1)*7,n*7)")
      calendar-cell(:cell="params")
</template>
<script lang="ts">
import { Cell } from '@/types'
import { reactive, defineComponent } from '@vue/composition-api'
import CalendarCell from '@/components/CalendarCell.vue'
import moment from 'moment'

function getDaysArray(year: number, month: number, cells: Cell[]) {
  const names = ['sun', 'mon', 'tue', 'wed', 'thu', 'fri', 'sat']
  const date = new Date(year, month - 1, 1)
  const result = []
  for (let i = 0; i < date.getDay(); i++)
    result.push({ day: '', dayOfTheWeek: names[date.getDay()] })
  while (date.getMonth() == month - 1) {
    const day = date.getDate()
    const cell = cells.find(el => el.day === day)
    result.push({
      day,
      badges: cell?.badges,
      dayOfTheWeek: names[date.getDay()]
    })
    date.setDate(day + 1)
  }
  for (let i = date.getDay(); i < 7; i++)
    result.push({ day: '', dayOfTheWeek: names[date.getDay()] })
  return result
}

export default defineComponent({
  components: { CalendarCell },
  props: {
    month: {
      type: Date,
      require: true,
      default: () => moment(Date.now()).toDate()
    },
    cells: {
      type: Array,
      require: true,
      default: () => [] as Cell[]
    }
  },
  setup(props) {
    const month = props.month as Date
    const data = props.cells as Cell[]
    const cells = getDaysArray(month.getFullYear(), month.getMonth() + 1, data)
    const state = reactive({
      cells,
      weekCount: Math.ceil(cells.length / 7) + 1
    })
    return { state }
  }
})
</script>
