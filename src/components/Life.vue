<template>
  <div class="life">
    <img src="../assets/images/heart.png" >
    <div class="teste">
      <span>{{life}}</span>
    </div>
    
  </div>
</template>

<script>
export default {
  props:{
    life:{type: Number, required: true}
  }
};
</script>

<style>
.life{
  position: fixed;
  top:10px;
  right: 10px;
  width: 50px;
  height: 50px;
}

.life img{
  width: 50px;
  height: 50px;
}

.life .teste{
  position: absolute;
  font-size: 1.5rem;
  font-weight: 600;
  top: 9px;
  left: 18px;
}
</style>