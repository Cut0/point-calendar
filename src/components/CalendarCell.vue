<template lang="pug">
v-card.cell-wrapper(
  outlined
  tile
  flat)
  div(:bind="{holiday:isHoliday,saturday:isSaturday}") {{cell.day}}
  template(v-for="badge in cell.badges")
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
.saturday {
  color: blue;
}
.holiday {
  color: red;
}
</style>
