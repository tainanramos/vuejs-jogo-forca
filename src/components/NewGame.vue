<template>
  <h1 class="iniciar" @click="newGame">Iniciar</h1>
</template>

<script>
export default {
  methods:{
    newGame(){
      this.$emit("newGame")
    }
  }
}
</script>

<style>
.iniciar{
  position: fixed;
  top: 20vh;
  font-size: 8rem;
  color: rgba(255, 255, 255, 0.3);
  cursor: pointer;
  transition: 0.7s;
}

.iniciar:hover{
  color: rgba(255, 255, 255, 1);
}
</style>