<script setup>
import { defineProps } from "vue";

defineProps({
  joke: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div v-if="joke.type == 'twopart'">
    <p className="setup">{{ joke.setup }}</p>
    <p className="delivery">{{ joke.delivery }}</p>
  </div>
  <p v-else >
    <p className="delivery">{{joke.joke}}</p>
  </p>
</template>

<style scoped>
p.setup {
  color: white;
  width: 90%;
  margin: 0 auto;
}

p.delivery {
  color: blue;
  width: 90%;
  margin: 0 auto;
}
</style>
