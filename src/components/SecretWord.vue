<template>
  <div class="visual-word">
    <div class="item-visual-word" v-for="word in visualWord" :key=word.index>
      {{ word.letter }}
    </div>
  </div>
</template>

<script>
export default {
  props:{
    visualWord: {type: Array, required: true}
  }
}
</script>

<style>
.visual-word{
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

.item-visual-word{
  margin: 10px;
  font-size: 5rem;
}
</style>