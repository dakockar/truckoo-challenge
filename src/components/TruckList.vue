<template>
  <search-bar @filter-list="filterList" @sort-list="sortList" />
  <div class="truck-list">
    <truck-card
      v-show="filteredTruckList.length"
      v-for="truck in filteredTruckList"
      :key="truck.uid"
      :truck="truck"
    />
    <p v-show="!filteredTruckList.length">No Result</p>
  </div>
</template>

<script>
import axios from "axios";
import TruckCard from "./TruckCard.vue";
import SearchBar from "./SearchBar.vue";

export default {
  components: { TruckCard, SearchBar },
  data() {
    return {
      truckList: [],
      filteredTruckList: [],
    };
  },
  methods: {
    filterList(searchText) {
      this.filteredTruckList = this.truckList.filter(
        (truck) =>
          truck.title.toLowerCase().includes(searchText.toLowerCase()) ||
          truck.tags.find((item) =>
            item.toLowerCase().includes(searchText.toLowerCase())
          )
      );
    },
    sortList(sortBy) {
      switch (sortBy) {
        case "date": {
          this.filteredTruckList.sort(
            (a, b) =>
              Date.parse(a.offerPublicationDate) -
              Date.parse(b.offerPublicationDate)
          );
          break;
        }
        case "priceAsc":
          this.filteredTruckList.sort((a, b) => a.highestBid - b.highestBid);
          break;
        case "priceDesc":
          this.filteredTruckList.sort((a, b) => b.highestBid - a.highestBid);
          break;
      }
    },
  },
  mounted() {
    axios
      .get(
        "https://truckoo-backend-aqkoiog6bq-ew.a.run.app/rest/v1/offers/active-offers"
      )
      .then((response) => {
        this.truckList = response.data;
        this.filteredTruckList = response.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style scoped>
.truck-list {
  display: flex;
  flex-wrap: wrap;
  box-sizing: border-box;
  justify-content: space-evenly;
  margin: 0;
  padding: 0 1rem;
  width: 100%;
}

p {
  margin-top: 50px;
  font-size: 2rem;
}
</style>