<template>
  <div class="top-head">
    <div>
      <img src="../assets/spotify-logo.png" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>

<style lang="scss" scoped>
.top-head {
  background-color: #2e3a46;
  display: flex;
  justify-content: flex-start;
}

img {
  width: 30px;
  height: 30px;
  margin: 10px;
}
</style>