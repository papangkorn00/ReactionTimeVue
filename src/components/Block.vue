<template>
  <div
    class="w-96 md:w-96 bg-pink-400 font-bold text-violet-600 text-center text-2xl py-16 px-4 m-10 md:m-20 mx-auto rounded-lg cursor-pointer"
    v-if="showBlock"
    @click="stopTimer"
  >
    click me
  </div>
</template>

<script setup>
import {ref, onMounted, defineProps, defineEmits} from "vue"

const props = defineProps(["delay"])
const emit = defineEmits()
const showBlock = ref(false)
const timer = ref(null)
const reactionTime = ref(0)

onMounted(() => {
  setTimeout(() => {
    showBlock.value = true
    startTimer()
  }, props.delay)
})

const startTimer = () => {
  timer.value = setInterval(() => {
    reactionTime.value += 10
  }, 10)
}

const stopTimer = () => {
  clearInterval(timer.value)
  emit("end", reactionTime.value)
}
</script>
