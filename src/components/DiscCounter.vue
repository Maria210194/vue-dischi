<template>
  <div>Items found: {{ number }}</div>
</template>

<script>
export default {
  name: "DiscCounter",
  props: {
    number: Number,
  },
};
</script>

<style scoped>
div {
  padding: 1rem;
}
</style>