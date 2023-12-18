<script setup>
import DiceBox from "./components/DiceBox.vue";
import Stats from "./components/Stats.vue";
import { ref } from "vue";

const ws = new WebSocket("ws://127.0.0.1:8080/ws/");

ws.onopen = () => {
  console.log("Connected to the WebSocket server!");
  ws.send("Hello from the client!");
};

ws.onmessage = (event) => {
  console.log(`Message Received: ${event.data}`);
};



const characterName = ref("");
const currentRoll = ref("");
const currentRollType = ref("");

function rollDice(roll) {
  currentRollType.value = roll.type;
  currentRoll.value = roll.roll;
  DiceBox.functions.rollDice(roll.roll);
}

function diceResult(results) {
  console.log(`${characterName.value} rolled ${currentRoll.value} as a ${currentRollType.value} check and got a ${results[0].value}!`)
  console.log(results);
}
</script>

<template>
  <div class="pure-g">
    <div class="pure-u-1-2">
      <h1>Character Sheet</h1>
      <label for="character-name">Character Name:</label>
      <input type="text" placeholder="Character Name" v-model="characterName" id="character-name" />
    </div>
    <div class="pure-u-1-2">
      <DiceBox @diceResult="diceResult" />
    </div>
  </div>
  <Stats v-on:diceRoll="rollDice"></Stats>
</template>
