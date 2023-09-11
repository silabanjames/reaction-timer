<template>
  <h1>Reaction Timer Games</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="stop" />
  <Reaction :score="score" v-if="showResult"/>
</template>

<script>
import Block from './components/Block.vue'
import Reaction from './components/Reaction.vue'

export default{
  data(){
    return{
      isPlaying: false,
      showResult: false,
      delay: null,
      score: null,
    }
  },
  components: { Block,Reaction },
  methods:{
    start(){
      this.isPlaying = true
      this.showResult = false
      this.delay = 2000 + Math.random() * 5000
    },
    stop(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult= true
    }
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

button{
  border-radius: 4px;
  background-color: rgb(67, 134, 67);
  color: rgb(255, 255, 255);
  border: none;
  font-size: 15px;
  padding: 5px 10px;
  margin: 20px auto;
}

button[disabled]{
  opacity: 0.5;
  cursor: not-allowed;
}

/* @media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
