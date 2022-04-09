<template>
  <div class="ms-card">
    <img :src="disc.poster" :alt="disc.author" />
    <h4>{{ disc.title }}</h4>
    <p>{{ disc.author }}</p>
    <p>{{ disc.year }}</p>
  </div>
</template>

<script>
/* Disc model
author: "Bon Jovi"
genre: "Rock"
poster: "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg"
title: "New Jersey"
year: "1988"
*/
export default {
  name: "DiscItem",
  props: {
    disc: Object,
  },
};
</script>

<style lang="scss" scoped>
.ms-card {
  width: 18%;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  justify-content: center;
  margin: 10px;
  background-color: #2e3a46;
  img {
    margin: 10px auto;
    width: 130px;
    height: 130px;
  }

  h4 {
    font-size: 20px;
    font-weight: 700;
  }
}
</style>