<template>
  <div>
    <input
      type="text"
      placeholder="Search"
      v-model.trim="inputText"
      @key.enter="performSearch"
    />
    <button @click="performSearch">Cerca</button>
    <select @change="showLabelValue($event)">
      <option value="Rock">Rock</option>
      <option value="Metal">Metal</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  data() {
    return {
      inputText: "",
      selectedLabel: "",
    };
  },
  methods: {
    performSearch() {
      this.$emit("search", this.inputText);
    },
    showLabelValue(event) {
      console.log(event);
      this.selectedLabel = event.genre.value;
      this.$emit("searchByGenre", this.selectedLabel);
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  margin-left: 0.5 rem;
  border-radius: 10px;
  padding: 2px 5px;
}
</style>