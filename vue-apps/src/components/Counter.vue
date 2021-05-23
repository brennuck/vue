<template>
  <div>
    <h2>Counter</h2>
    {{ count }}
  </div>
  <div>
    <button @click="$emit('add-count', count)">Up</button>
    <button @click="$emit('down-count', count)">Down</button>
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: ["count"],
};
</script>

<style scoped>
button {
  margin-top: 20px;
}
</style>