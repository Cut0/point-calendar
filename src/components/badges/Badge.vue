<template lang="pug">
div.badge-wrapper(:style="{ 'background-color': color}") 
  span {{value}}
</template>
<script lang="ts">
import { defineComponent } from '@vue/composition-api'
export default defineComponent({
  props: {
    value: { type: String },
    color: { type: String }
  }
})
</script>
<style scoped>
.badge-wrapper {
  margin: 2px 12px;
  border-radius: 5%;
}
</style>
