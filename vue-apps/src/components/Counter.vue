<template>
  <div>
    <h2>Counter</h2>
    <p
      class="number"
      v-bind:style="[count === 0 ? 'color: green' : 'color: black']"
    >
      {{ count }}
    </p>
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
p {
    font-size: 30px;
}
</style>