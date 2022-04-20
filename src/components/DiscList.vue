<template>
  <div class="container mx-5">
    <div class="col-12">
      <SearchComponent @search="filterByName" @searchByGenre="filterByGenre" />
      <DiscCounter :number="discNumber" />
    </div>
    <div v-if="!isLoading" class="row">
      <DiscItem v-for="item in filteredList" :key="item.author" :disc="item" />
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
import SearchComponent from "@/components/SearchComponent.vue";
import DiscCounter from "@/components/DiscCounter.vue";

export default {
  name: "DiscList",
  data() {
    return {
      discs: [],
      searchText: "",
      genre: "",
    };
  },
  props: {
    url: String,
  },
  computed: {
    isLoading() {
      return this.discs.length === 0;
    },
    filteredList() {
      if (this.searchText.length === 0 && this.genre.length === 0) {
        return this.discs;
      }
      const filtered = this.discs.filter((item) => {
        return item.genre.toLowerCase().includes(this.genre.toLowerCase());
      });
      return filtered.filter(
        (item) =>
          item.author.toLowerCase().includes(this.searchText.toLowerCase()) ||
          item.genre.toLowerCase().includes(this.searchText.toLowerCase())
      );
    },
    discNumber() {
      return this.filteredList.length;
    },
  },
  components: {
    DiscItem,
    LoadingComponent,
    SearchComponent,
    DiscCounter,
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
    filterByName(searchText) {
      console.log(searchText);
      this.searchText = searchText;
    },
    filterByGenre(genre) {
      this.genre = genre;
    },
  },
};
</script>

<style lang="scss" scoped>
</style>