<template>
  <div class="py-4">
    <p class="text-xl">
      Your Reaction Time is: {{ score }} ms / {{ score / 1000 }} s
    </p>
  </div>
</template>
<script setup>
const props = defineProps(["score"])
</script>
