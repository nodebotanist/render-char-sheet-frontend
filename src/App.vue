<script setup>
import DiceBox from "./components/DiceBox.vue";
import Stats from "./components/Stats.vue";

function rollDice(value) { 
  DiceBox.functions.rollDice(value);
}
</script>

<template>
  <div class="pure-g" >
    <div class="pure-u-1-2">
      <h1>Character Sheet</h1>
      <label for="character-name">Character Name:</label>
      <input type="text" placeholder="Character Name" id="character-name" />
    </div>
    <div class="pure-u-1-2">
      <DiceBox />
    </div>
  </div>
  <Stats v-on:diceRoll=rollDice></Stats>
</template>
