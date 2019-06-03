<template>
  <div class="home">
    <img v-if="isOn" class="bulb-image" src="../assets/bulbOn.jpg">
    <img v-else class="bulb-image" src="../assets/bulbOff.jpg">
    <button :disabled="isOn" @click="isOn=true">켜기</button>
    <button :disabled="!isOn" @click="test()">끄기</button>
  </div>
</template>

<script>
import 'expose-loader?$!expose-loader?jQuery!jquery'
import WebIOPi from '../webiopi.js'

export default {
  data () {
    return {
      isOn: true
    }
  },
  methods: {
    test() {
      let w = new WebIOPi()
      w.ready(function() {
        w.callMacro("go_forward");
      });

    },
    test2() {
          let w = new WebIOPi()
          w.ready(function() {
            w.callMacro("go_backward");
          });
    }
  }
}
</script>

<style scoped>
  .bulb-image {
    width: 300px;
    height: 300px;
  }
</style>
