<script setup>
import MainScreen from "./components/MainScreen.vue"
import InteractScreen from "./components/InteractScreen.vue"
import { ref } from "vue"
import { shuffled } from './utils/array.js'

const statusMatch = ref("default");
const settings = ref({
  totalOfBlocks: 0,
  cardsContext: [],
  startedAt: null
});

const onHandleBeforeStart = (config) => {
  settings.value.totalOfBlocks = config;
  const firstCards = Array.from({ length: settings.value.totalOfBlocks / 2}, (_, i) => i + 1);
  const secondCards = [...firstCards];
  const cards = [...firstCards, ...secondCards];
  settings.value.cardsContext = shuffled(shuffled(shuffled(shuffled(cards))));
  settings.value.startedAt = new Date().getTime();
  statusMatch.value = "match";
}
</script>

<template>
<MainScreen v-if="statusMatch === 'default'" @on-start="onHandleBeforeStart"/>
<InteractScreen v-if="statusMatch === 'match'" :cardsContext="settings.cardsContext" />
</template>

<style scoped>

</style>
