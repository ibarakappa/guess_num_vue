<script>
import GuessNum from "./components/GuessNum.vue";
export default {
   components: {
      GuessNum,
   },
};
</script>

<template>
   <div class="guess-area">
      <GuessNum></GuessNum>
   </div>
</template>

<style lang="scss" scoped>
.guess-area {
   width: 100vw;
   height: 100vh;
   display: flex;
   justify-content: center;
   align-items: center;
}
</style>
