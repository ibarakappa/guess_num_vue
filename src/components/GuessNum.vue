<script>
export default {
   data() {
      return {
         lowNum: 1,
         highNum: 100,
         guessNum: null,
         ans: Math.floor(Math.random() * 100) + 1,

         trigger: 1,
      };
   },
   methods: {
      checkNum() {
         this.trigger = 1;
         if (this.guessNum === this.ans) {
            this.trigger = 0;
         } else if (this.guessNum < this.ans && this.guessNum > this.lowNum) {
            this.lowNum = this.guessNum;
         } else if (this.guessNum > this.ans && this.guessNum < this.highNum) {
            this.highNum = this.guessNum;
         } else {
            this.trigger = 2;
         }
         this.guessNum = null;
      },
      checkScope() {
         if (this.trigger == 1 || this.trigger == 2) {
            return true;
         }
         return false;
      },
   },
   mounted() {},
};
</script>

<template>
   <div class="card-area">
      <h1 v-if="trigger == 1">猜數字</h1>
      <h1 v-if="trigger == 0">恭喜答對了</h1>
      <h1 v-if="trigger == 2">請猜範圍內的數字</h1>
      <div class="num-area d-flex">
         <div class="check-area d-flex" v-if="checkScope()">
            <p>{{ lowNum }}</p>
            <p>-</p>
            <p>{{ highNum }}</p>
         </div>

         <p v-if="trigger == 0">{{ ans }}</p>
      </div>

      <input placeholder="TEST" type="number" v-model="guessNum" />
      <button type="button" @click="checkNum()">回答</button>
   </div>
</template>

<style lang="scss" scoped>
.card-area {
   width: 40vw;
   height: 80vh;
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
   .num-area {
      p {
         margin: 1rem 1rem;
      }
   }
   button {
      margin-top: 1rem;
   }
}
</style>
