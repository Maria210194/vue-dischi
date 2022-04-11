<template>
  <div>
    <input
      type="text"
      placeholder="Search"
      v-model.trim="inputText"
      @key.enter="performSearch"
    />
    <button @click="performSearch">Cerca</button>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  data() {
    return {
      inputText: "",
    };
  },
  methods: {
    performSearch() {
      this.$emit("search", this.inputText);
    },
  },
};
</script>

<style>
</style>