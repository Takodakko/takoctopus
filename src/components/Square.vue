<script setup lang="ts">
import { computed } from 'vue'
import Piece from './Piece.vue'
//import {tileKeys} from '../App.vue'

// defineProps<{ tileNumber: string, piecePositions: Object }>()
const props = defineProps({
  tileNumber: {type: String, required: true},
  piecePositions: {type: Object, required: true},

});
//const tileNumber: tileKeys = props.tileNumber;
const emit = defineEmits(['toggle-active-piece']);
const { tileNumber, piecePositions } = props;
const isChosen = computed(() => piecePositions[tileNumber][1]);

const here: string = piecePositions[tileNumber][0];
const containsRedKing = computed(() => here === 'redKing');
const containsCyanKing = computed(() => here === 'cyanKing');
const containsRedPawn = computed(() => here === 'redPawn');
const containsCyanPawn = computed(() => here === 'cyanPawn');
function chosePiece() {
  emit('toggle-active-piece', props.tileNumber);
  console.log('emtted from tile', props.tileNumber);
}

const emptySquareCss = 'bg-white border-solid border-black border-2 max-w-xs min-w-20 max-h-14 min-h-20';
</script>

<template>
  <div :class="emptySquareCss">
    {{tileNumber}}
    <Piece v-if="containsRedKing" color="red" type="king" @chose-piece="chosePiece" :isChosen="isChosen"/>
    <Piece v-if="containsCyanKing" color="cyan" type="king" @chose-piece="chosePiece" :isChosen="isChosen"/>
    <Piece v-if="containsRedPawn" color="red" type="pawn" @chose-piece="chosePiece" :isChosen="isChosen"/>
    <Piece v-if="containsCyanPawn" color="cyan" type="pawn" @chose-piece="chosePiece" :isChosen="isChosen"/>
  </div>
</template>

<style scoped>

</style>