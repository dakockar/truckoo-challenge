<template>
  <div class="index-page">
    <truck-list />
  </div>
</template>

<script>
import TruckList from "./TruckList.vue";

export default {
  components: {
    TruckList,
  },
};
</script>

<style scoped>
.index-page {
  width: 100%;
  margin-left: 300px;
  padding: 0 4rem;
}
</style>
