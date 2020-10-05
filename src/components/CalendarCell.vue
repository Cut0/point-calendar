<template lang="pug">
.cell-wrapper
  div(:bind="{holiday:isHoliday,saturday:isSaturday}") {{cell.day}}
  .badges-cover(v-for="badge in cell.badges")
    badge(:value="badge.value" :color="badge.color")
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'
import Badge from './badges/Badge.vue'
export default defineComponent({
  components: { Badge },
  props: {
    cell: {
      type: Object
    },
    isSaturday: {
      type: Boolean
    },
    isHoliday: {
      type: Boolean
    }
  }
})
</script>

<style scoped>
.cell-wrapper {
  height: 80px;
  text-align: center;
}
.badges-cover {
  display: flex;
  justify-content: center;
  align-items: center;
}
.saturday {
  color: blue;
}
.holiday {
  color: red;
}
</style>
