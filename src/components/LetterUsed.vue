<template>
  <div class="used">
    <div v-for="(letter, i) in used" :key="i" class="item-used" :class="classLetter(letter.found)">
      {{ letter.letter }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    used: { type: Array, required: true },
  },
  methods:{
    classLetter(found){
      return found ? "found-true" : "found-false"
    }
  }
};
</script>

<style>
.used {
  display: flex;
  justify-content: center;
  margin: 10px;
}

.item-used{
  margin: 10px 5px;
  border: 1px solid #fff;
  padding: 5px 10px;
  font-size: 1.5rem;
  border-radius: 8px;
}

.used .found-true{
  background-color: rgb(4, 146, 4);
}

.used .found-false{
  background-color: rgb(180, 8, 8);
}
</style>