<template>
  <div class="input-letter">
    <input
      v-model="word"
      @keydown.end="showSecret"
      @keydown.enter="findLetter"
      class="form-element"
      placeholder="Insira uma letra"
      type="text"
      autofocus
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      word: "",
    };
  },
  methods:{
    findLetter(){
      this.$emit("findLetter", this.word)
      this.word = ""
    },
    showSecret(){
      this.$emit("showSecret")
    }
  }
}   
</script>

<style>
.input-letter {
  display: flex;
  justify-content: center;
  margin: 35px;
}

.form-element {
  outline: none;
  font-size: 1.5rem;
  border: 1px solid #fff;
  padding: 5px 10px 8px;
  color: #fff;
}

input.form-element {
  width: 250;
  background-color: #fff2;
  border-radius: 8px;
}
</style>
