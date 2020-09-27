<template lang="pug">
div.badge-wrapper(:style="{ 'background-color': color}") 
  span.value {{value}}
</template>
<script lang="ts">
import { defineComponent } from '@vue/composition-api'
export default defineComponent({
  props: {
    value: { type: Number },
    color: { type: String }
  }
})
</script>
<style scoped>
.value {
  font-size: 12px;
}
.badge-wrapper {
  height: 18px;
  margin: 2px 12px;
  border-radius: 4px !important;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
