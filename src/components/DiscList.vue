<template>
  <div class="container mx-5">
    <div v-if="discs.length > 0" class="row">
      <DiscItem v-for="item in discs" :key="item.author" :disc="item" />
    </div>
    <div v-else>
      <LoadingComponent />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import DiscItem from "@/components/DiscItem.vue";
import LoadingComponent from "@/components/LoadingComponent.vue";

export default {
  name: "DiscList",
  data() {
    return {
      discs: [],
    };
  },
  props: {
    url: String,
  },
  components: {
    DiscItem,
    LoadingComponent,
  },

  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      axios
        .get(this.url)
        .then((response) => {
          console.log(response);
          if (response.status === 200) {
            this.discs = response.data.response;
            console.log(this.discs[0]);
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