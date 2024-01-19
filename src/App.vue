<template>
  <div class="min-h-screen flex flex-col items-center justify-center">
    <h1 class="text-5xl font-bold mb-8">Reaction Time</h1>
    <button class="btn btn-primary" @click="start" :disabled="isPlaying">
      Play
    </button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Result v-if="showResults" :score="score" />
  </div>
</template>

<script setup>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"
import {ref} from "vue"

const isPlaying = ref(false)
const delay = ref(null)
const score = ref(null)
const showResults = ref(false)

const start = () => {
  delay.value = 2000 + Math.random() * 5000
  isPlaying.value = true
  showResults.value = false
}

const endGame = (reactionTime) => {
  score.value = reactionTime
  isPlaying.value = false
  showResults.value = true
}
</script>
