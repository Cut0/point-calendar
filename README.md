calendarに数値を表示できます

# Usage

## npm

```
yarn add point-calendar
```
```
npm install point-calendar
```

## GitHub Package Registry

```
<template lang="pug">
#app
  point-calendar(
    :month="state.date"
    :cells="state.cells"
  )
</template>
<script lang="ts">
import { reactive, defineComponent } from '@vue/composition-api'
import moment from 'moment'
import PointCalendar from '@/components/PointCalendar.vue'
export default defineComponent({
  components: { PointCalendar },
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

```