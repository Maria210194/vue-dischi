<template>
  <div id="app">
    <HeaderComponent />
    <DiscList :url="apiUrl" />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import DiscList from "./components/DiscList.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    DiscList,
  },
  data() {
    return {
      apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
    };
  },
};
</script>

<style lang="scss">
@import "@/style/general";
@import "@/style/variables";

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
