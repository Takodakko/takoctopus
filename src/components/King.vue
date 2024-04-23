<script setup lang="ts">
//import { ref } from 'vue'

const props = defineProps({
  color: {type: String, required: true}
});
const pieceColor = `bg-${props.color}-500`;

</script>

<template>
  <div :class=pieceColor>
    hi
  </div>
</template>

<style scoped>

</style>
