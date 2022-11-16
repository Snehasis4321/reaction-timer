<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer:null,
      reactionTime:0
    };
  },
  mounted() {
    console.log("component Mounted"),
      setTimeout(() => {
        (this.showBlock = true),this.startTimer(), console.log(this.delay);
      }, this.delay);
  },
  methods:{
    startTimer(){
        this.timer=setInterval(()=>{
            this.reactionTime+=10
        },10)
    },
    stopTimer(){
        clearInterval(this.timer)
        this.$emit('end',this.reactionTime)
    }
  },
  updated() {
    console.log("component Updated");
  },
  unmounted() {
    console.log("component UnMounted");
  },
};
</script>

<style>
.block {
  width: 350px;
  border-radius: 20px;
  background: #0984e3;
  color: white;
  font-size: 1.5rem;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
