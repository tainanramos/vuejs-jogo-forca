<template>
  <div class="game-over">
    <h2>Game Over</h2>
    <h2 class="reset" @click="newGame">Novo Jogo</h2>
  </div>
</template>

<script>
export default {
  methods: {
    newGame() {
      this.$emit("newGame");
    },
  },
};
</script>

<style>
.game-over{
  display: flex;
  flex-direction: column;
  font-size: 2rem;
  color: rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition: 0.7s;
  text-align: center;
}

.reset:hover{
  color: rgba(255, 255, 255, 1);
}
</style>