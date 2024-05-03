<script setup lang="ts">
import { ref } from 'vue'
import Square from './components/Square.vue'

// const redKingPosition = '3-4';
// const redPawnPosition = '1-1';
//export type tileKeys = '1-1' | '1-2' | '1-3' | '1-4' | '1-5' | '2-1' | '2-2' | '2-3' | '2-4' | '2-5' | '3-1' | '3-2' | '3-3' | '3-4' | '3-5' | '4-1' | '4-2' | '4-3' | '4-4' | '4-5' | '5-1' | '5-2' | '5-3' | '5-4' | '5-5';
// interface IPiecePositions {
//   [key: tileKeys] : Array<string | boolean>;
// }
const initialPiecePositions: Record<string, Array<string | boolean>> = {
  '1-1': ['empty', false],
  '1-2': ['empty', false],
  '1-3': ['cyanKing', false],
  '1-4': ['cyanPawn', false],
  '1-5': ['empty', false],
  '2-1': ['empty', false],
  '2-2': ['empty', false],
  '2-3': ['empty', false],
  '2-4': ['empty', false],
  '2-5': ['empty', false],
  '3-1': ['empty', false],
  '3-2': ['empty', false],
  '3-3': ['empty', false],
  '3-4': ['empty', false],
  '3-5': ['empty', false],
  '4-1': ['empty', false],
  '4-2': ['empty', false],
  '4-3': ['empty', false],
  '4-4': ['empty', false],
  '4-5': ['empty', false],
  '5-1': ['empty', false],
  '5-2': ['redPawn', false],
  '5-3': ['redKing', false],
  '5-4': ['empty', false],
  '5-5': ['empty', false],
};

function setActivePiece(tileNumber: string) {
  for (let tile in piecePositions.value) {
    const current = piecePositions.value[tile];
    console.log(current, 'current');
    current[1] = false;
  }
  piecePositions.value[tileNumber][1] = true;
  console.log(piecePositions.value[tileNumber][1]);
};

const piecePositions = ref(initialPiecePositions);

const rowCss = 'flex flex-row p-0';
</script>

<template>
  <div v-for="row in 5" :class="rowCss">
    <Square v-for="n in 5" :piece-positions="piecePositions" :tile-number="`${row.toString()}-${n.toString()}`" :key="`${row.toString()}-${n.toString()}`" @toggleActivePiece="setActivePiece"/>
  </div>
  
</template>

<style scoped>

</style>
