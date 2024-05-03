<script setup lang="ts">
import { computed, ref } from 'vue'
import Piece from './Piece.vue'

// defineProps<{ tileNumber: string, piecePositions: Object }>()
const props = defineProps({
  tileNumber: {type: String, required: true},
  piecePositions: {type: Object, required: true},

});
const emit = defineEmits(['toggle-active-piece']);
const { tileNumber, piecePositions } = props;
const isChosen = ref(false);

const here = piecePositions[tileNumber];
const containsRedKing = computed(() => here === 'redKing');
const containsCyanKing = computed(() => here === 'cyanKing');
const containsRedPawn = computed(() => here === 'redPawn');
const containsCyanPawn = computed(() => here === 'cyanPawn');
function chosePiece() {
  isChosen.value = !isChosen.value
}

const emptySquareCss = 'bg-white border-solid border-black border-2 max-w-xs min-w-20 max-h-14 min-h-20';
</script>

<template>
  <div :class="emptySquareCss">
    {{tileNumber}}
    <Piece v-if="containsRedKing" color="red" type="king" @chose-piece="chosePiece"/>
    <Piece v-if="containsCyanKing" color="cyan" type="king"/>
    <Piece v-if="containsRedPawn" color="red" type="pawn"/>
    <Piece v-if="containsCyanPawn" color="cyan" type="pawn"/>
  </div>
</template>

<style scoped>

</style>