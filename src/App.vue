<script setup>
import DiceBox from "./components/DiceBox.vue";
import Stats from "./components/Stats.vue";
import { ref } from "vue";

const ws = new WebSocket("wss://character-sheet-backend.onrender.com");

ws.onopen = () => {
  console.log("Connected to the WebSocket server!");
};

ws.onmessage = (event) => {
  console.log(`Message Received: ${event.data}`);
  let rolls = event.data.replace( /"/g, '').split(",");
  let rollsBox = document.getElementById("rolls-box");
  rollsBox.innerHTML = "";
  rolls.reverse().forEach((roll) => {
    let rollBox = document.createElement("li");
    rollBox.innerText = roll;
    rollsBox.appendChild(rollBox);
  });
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
  ws.send(`${characterName.value || "Someone"} rolled ${currentRoll.value} as a ${currentRollType.value} check and got a ${results[0].value}!`)
}
</script>

<template>
  <DiceBox @diceResult="diceResult" />
  <div class="pure-g">
    <div class="pure-u-1">
      <h1>Character Sheet</h1>
      <label for="character-name">Character Name:</label>
      <input type="text" placeholder="Character Name" v-model="characterName" id="character-name" />
    </div>
  </div>
  <Stats v-on:diceRoll="rollDice"></Stats>
  <ul id="rolls-box"></ul>
</template>
