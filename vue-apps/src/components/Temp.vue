<template>
  <div>
      <h3>Salt Lake's current temperature</h3>
      <h4>{{ info * 9 / 5 + 32 + "°" }}</h4>
  </div>
</template>

<script>
export default {
  name: "Temp",
  props: ["info"]
};
</script>

<style scoped>
</style>