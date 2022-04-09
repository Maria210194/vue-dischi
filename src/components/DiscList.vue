<template>
  <div class="container">esisto</div>
</template>

<script>
import axios from "axios";

export default {
  name: "DiscList",
  data() {
    return {
      discs: [],
    };
  },
  props: {
    disc: Object,
  },
  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      axios
        .get(this.disc)
        .then((response) => {
          console.log(response);
          if (response.status === 200) {
            this.discs = response.data;
            // console.log(this.discs[0]);
          }
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
</style>