<template>
  <div class="home">
    <img v-if="isOn" class="bulb-image" src="../assets/bulbOn.jpg">
    <img v-else class="bulb-image" src="../assets/bulbOff.jpg">
    <button :disabled="isOn" @click="isOn=true">켜기</button>
    <button :disabled="!isOn" @click="isOn=false">끄기</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isOn: true
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