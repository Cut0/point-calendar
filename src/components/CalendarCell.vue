<template lang="pug">
v-card.cell-wrapper(
  outlined
  tile
  flat)
  div(:bind="{holiday:isHoliday,saturday:isSaturday}") {{day}}
  badge(value="12" color="red")
</template>

<script lang="ts">
import { reactive, defineComponent } from '@vue/composition-api'
import Badge from './badges/Badge.vue'
export default defineComponent({
  components: { Badge },
  props: {
    day: {},
    isSaturday: {
      type: Boolean
    },
    isHoliday: {
      type: Boolean
    }
  },
  setup() {
    const state = reactive({})
    return { state }
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
