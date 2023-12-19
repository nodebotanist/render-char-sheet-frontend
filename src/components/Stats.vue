<script setup>
import { ref, defineEmits } from "vue";

const str = ref(10);
const dex = ref(10);
const con = ref(10);
const int = ref(10);
const wis = ref(10);
const cha = ref(10);

const diceRollEvent = defineEmits(["diceRoll"]);
function emitDiceRollEvent(value) {
  diceRollEvent("diceRoll", value);
}
</script>

<template>
  <div class="pure-g" id="stats">
    <div class="pure-u-1"><h2>Stats</h2></div>
    <div class="pure-u-1-2">
      <span>Strength: </span>
      <button class="button-error pure-button" @click.prevent:="str--">
        -
      </button>
      <span>{{ str }}</span>
      <button class="button-success pure-button" @click.prevent:="str++">
        +
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Strength modifier: {{ Math.floor((str - 10) / 2) }}</span>
      <button
        @click="
          emitDiceRollEvent({
            type: 'Strength',   
            roll: '1d20' +
              (Math.floor((str - 10) / 2) == 0
                ? ''
                : (Math.floor((str - 10) / 2) > 0 ? ('+' + Math.floor((str - 10) / 2)) : ( Math.floor((str - 10) / 2))))
          })
        "
      >
        Roll
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Dexterity</span>
      <button class="button-error pure-button" @click.prevent:="dex--">
        -
      </button>
      <span>{{ dex }}</span>
      <button class="button-success pure-button" @click.prevent:="dex++">
        +
      </button>
    </div>
    <div class="pure-1-2">
      <span>Dexterity modifier: {{ Math.floor((dex - 10) / 2) }}</span>
      <button
        @click="
          emitDiceRollEvent({
            type: 'Dexterity',   
            roll: '1d20' +
              (Math.floor((str - 10) / 2) == 0
                ? ''
                : (Math.floor((str - 10) / 2) > 0 ? ('+' + Math.floor((str - 10) / 2)) : ( Math.floor((str - 10) / 2))))
          })
        "
      >
        Roll
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Constitution</span>
      <button class="button-error pure-button" @click.prevent:="con--">
        -
      </button>
      <span>{{ con }}</span>
      <button class="button-success pure-button" @click.prevent:="con++">
        +
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Constitution modifier: {{ Math.floor((con - 10) / 2) }}</span>
      <button
        @click="
          emitDiceRollEvent({
            type: 'Constitution',   
            roll: '1d20' +
              (Math.floor((str - 10) / 2) == 0
                ? ''
                : (Math.floor((str - 10) / 2) > 0 ? ('+' + Math.floor((str - 10) / 2)) : ( Math.floor((str - 10) / 2))))
          })
        "
      >
        Roll
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Intelligence</span>
      <button class="button-error pure-button" @click.prevent:="int--">
        -
      </button>
      <span>{{ int }}</span>
      <button class="button-success pure-button" @click.prevent:="int++">
        +
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Intelligence modifier: {{ Math.floor((int - 10) / 2) }}</span>
      <button
        @click="
          emitDiceRollEvent({
            type: 'Intelligence', 
            roll: '1d20' +
              (Math.floor((str - 10) / 2) == 0
                ? ''
                : (Math.floor((str - 10) / 2) > 0 ? ('+' + Math.floor((str - 10) / 2)) : ( Math.floor((str - 10) / 2))))
          })
        "
      >
        Roll
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Wisdom</span>
      <button class="button-error pure-button" @click.prevent:="wis--">
        -
      </button>
      <span>{{ wis }}</span>
      <button class="button-success pure-button" @click.prevent:="wis++">
        +
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Wisdom modifier: {{ Math.floor((wis - 10) / 2) }}</span>
      <button
        @click="
          emitDiceRollEvent({
            type: 'Wisdom',   
            roll: '1d20' +
              (Math.floor((str - 10) / 2) == 0
                ? ''
                : (Math.floor((str - 10) / 2) > 0 ? ('+' + Math.floor((str - 10) / 2)) : ( Math.floor((str - 10) / 2))))
          })
        "
      >
        Roll
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Charisma</span>
      <button class="button-error pure-button" @click.prevent:="cha--">
        -
      </button>
      <span>{{ cha }}</span>
      <button class="button-success pure-button" @click.prevent:="cha++">
        +
      </button>
    </div>
    <div class="pure-u-1-2">
      <span>Charisma modifier: {{ Math.floor((cha - 10) / 2) }}</span>
      <button
        @click="
          emitDiceRollEvent({
            type: 'Charisma',   
            roll: '1d20' +
              (Math.floor((str - 10) / 2) == 0
                ? ''
                : (Math.floor((str - 10) / 2) > 0 ? ('+' + Math.floor((str - 10) / 2)) : ( Math.floor((str - 10) / 2)))),
          })
        "
      >
        Roll
      </button>
    </div>
  </div>
</template>
