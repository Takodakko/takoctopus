<script setup lang="ts">
import { ref } from 'vue'
//import King from './components/King.vue'
import Square from './components/Square.vue'

// const redKingPosition = '3-4';
// const redPawnPosition = '1-1';

const initialPiecePositions = {
  '1-1': 'empty',
  '1-2': 'empty',
  '1-3': 'cyanKing',
  '1-4': 'cyanPawn',
  '1-5': 'empty',
  '2-1': 'empty',
  '2-2': 'empty',
  '2-3': 'empty',
  '2-4': 'empty',
  '2-5': 'empty',
  '3-1': 'empty',
  '3-2': 'empty',
  '3-3': 'empty',
  '3-4': 'empty',
  '3-5': 'empty',
  '4-1': 'empty',
  '4-2': 'empty',
  '4-3': 'empty',
  '4-4': 'empty',
  '4-5': 'empty',
  '5-1': 'empty',
  '5-2': 'redPawn',
  '5-3': 'redKing',
  '5-4': 'empty',
  '5-5': 'empty',
};

const piecePositions = ref(initialPiecePositions);

const rowCss = 'flex flex-row p-0';
</script>

<template>
  <div v-for="row in 5" :class="rowCss">
    <Square v-for="n in 5" :piece-positions="piecePositions" :tile-number="`${row.toString()}-${n.toString()}`" :key="`${row.toString()}-${n.toString()}`"/>
  </div>
  
</template>

<style scoped>

</style>
