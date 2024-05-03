<script setup lang="ts">
import { computed } from 'vue'
import images from '../pieceImageList';

const { LightPawn, LightKing } = images;

const props = defineProps({
  color: {type: String, required: true},
  type: {type: String, required: true},
  isChosen: {type: Boolean, required: true},
});

const imageUrl = props.type === 'king' ? LightKing : LightPawn;
const emit = defineEmits(['chose-piece']);
const pieceColor = computed(() => `bg-${props.color}-500 max-w-6 max-h-6`);
const chosenBorder = computed(() => props.isChosen ? 'border-solid border-black border-2' : null);
const pieceCss = computed(() => {
  return chosenBorder.value ? chosenBorder.value : '';
});

const pieceName = `${props.color} ${props.type.slice(0, -3)}`;
const choosePiece = function() {
  console.log('clicked piece');
  emit('chose-piece');
}
console.log(pieceName, props.isChosen, 'isChosen?')
</script>

<template>
  <div :class="pieceCss" @click="choosePiece">
    {{pieceName}}
    <img :src="imageUrl" :class="pieceColor">
  </div>
</template>

<style scoped>

</style>
