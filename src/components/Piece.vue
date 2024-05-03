<script setup lang="ts">
//import { ref } from 'vue'

const props = defineProps({
  color: {type: String, required: true},
  type: {type: String, required: true}
});
const emit = defineEmits(['chose-piece']);
const pieceColor = `bg-${props.color}-500`;
const pieceName = `${props.color} ${props.type}`;
const choosePiece = function() {
  emit('chose-piece');
}

</script>

<template>
  <div :class=pieceColor @click="choosePiece">
    {{pieceName}}
  </div>
</template>

<style scoped>

</style>
