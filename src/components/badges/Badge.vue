<template lang="pug">
.badge-wrapper(:style="{ 'background-color': color}") 
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
  width: 100%;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
