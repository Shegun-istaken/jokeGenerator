<script setup>
import { reactive } from "vue";
import FormatJoke from "@/components/formatJoke.vue";
import Keypress from "vue-keypress";

const state = reactive({
  details: "",
});

async function fetchJoke() {
  const response = await fetch(
    "https://v2.jokeapi.dev/joke/Any?blacklistFlags=racist"
  );

  state.details = await response.json();

  var synthesis = window.speechSynthesis;
  var utterance = new SpeechSynthesisUtterance(
    state.details.type == "twopart"
      ? ` ${state.details?.setup} ${state.details.delivery}`
      : `${state.details.joke}`
  );

  synthesis.speak(utterance);
}
</script>

<template>
  <Keypress key-event="keyup" :key-code="74" @success="fetchJoke" />
  <div class="generateJoke" tabindex="-1" @keyup.enter="console.log('hello')">
    <button @click="fetchJoke">Click Here or Press 'J' to hear a Joke</button>
    <div></div>
    <FormatJoke v-if="state.details" :joke="state.details" />
  </div>
</template>

<style scoped>
div.generateJoke button {
  margin: 40px 0 20px 0;
  background-color: white;
  padding: 16px 24px;
  border-radius: 8px;
}
</style>
