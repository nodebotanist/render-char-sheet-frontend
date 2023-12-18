<script>
import { onMounted, defineEmits } from "vue";
import DiceBox from "https://unpkg.com/@3d-dice/dice-box@1.0.8/dist/dice-box.es.min.js";

let Box = new DiceBox("#dice-box", {
  assetPath: "assets/",
  origin: "https://unpkg.com/@3d-dice/dice-box@1.0.8/dist/",
  theme: "default",
  themeColor: "#feea03",
  offscreen: true,
  scale: 6,
});

let isRolling = true; 

function rollDice(value) {
  if (Box && Box.roll && !isRolling) {
    isRolling = true;
    Box.roll(value);
  } else {
    alert("Dice box not ready yet!")
  }
}

export default {
  components: {
    DiceBox,
  },
  functions: {
    rollDice,
  },
  emits: ["diceResult"],
  setup: (props, {emit}) => {
    onMounted(() => {
      Box.init().then(async (world) => {
        isRolling = false;
      });
    });

    Box.onRollComplete = (results) => {
      isRolling = false;      
      emit("diceResult", results)
    };

    function announceResults(results){
      diceResultEvent("diceResult", results);
    }
  },
};
</script>

<template>
  <div id="dice-box"></div>
</template>
