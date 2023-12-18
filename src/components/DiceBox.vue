<script>
import { onMounted } from "vue";
import DiceBox from "https://unpkg.com/@3d-dice/dice-box@1.0.8/dist/dice-box.es.min.js";

let Box = new DiceBox("#dice-box", {
  assetPath: "assets/",
  origin: "https://unpkg.com/@3d-dice/dice-box@1.0.8/dist/",
  theme: "default",
  themeColor: "#feea03",
  offscreen: true,
  scale: 6,
});

function rollDice(value) {
  if (Box && diceBoxContext) {
    Box.roll(value);
  } else {
  }
}

export default {
  components: {
    DiceBox,
  },
  functions: {
    rollDice,
  },
  setup: () => {
    onMounted(() => {
      Box.init().then(async (world) => {
        Box.onRollComplete = (results) => {
          console.log(results);
        };
      });
    });
  },
};
</script>

<template>
  <div id="dice-box"></div>
</template>
