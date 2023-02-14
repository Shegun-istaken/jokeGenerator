<script setup>
import laugh from "@/assets/laugh.gif";
import JokeGen from "@/components/JokeGen.vue";
</script>

<template>
  <main className="joke">
    <img :src="laugh" alt="" />
    <JokeGen />
  </main>
</template>

<style scoped>
main.joke {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 60%;
  text-align: center;
  margin: 88px auto 0 auto;
}
</style>
