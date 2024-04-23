<script setup lang="ts">
import { computed } from 'vue'
import King from './King.vue'

// defineProps<{ tileNumber: string, piecePositions: Object }>()
const props = defineProps({
  tileNumber: {type: String, required: true},
  piecePositions: {type: Object, required: true},

});
const { tileNumber, piecePositions } = props;

const here = piecePositions[tileNumber];
const containsRedKing = computed(() => here === 'redKing');
const containsCyanKing = computed(() => here === 'cyanKing');
//const count = ref(0)

const emptySquareCss = 'bg-white border-solid border-black border-2 max-w-xs min-w-20 max-h-14 min-h-20';
</script>

<template>
  <div :class="emptySquareCss">
    {{tileNumber}}
    <King v-if="containsCyanKing" color="pink"/>
    <King v-if="containsRedKing" color="red"/>
  </div>
</template>

<style scoped>

</style>