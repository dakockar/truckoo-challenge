<template>
  <div class="truck-card">
    <img :src="truck.vehicle_picture_front" :alt="truck.title" />
    <div class="truck-card-body">
      <h2>{{ truck.title }}</h2>
      <ul class="tag-list">
        <li class="tag" v-for="tag in truck.tags" :key="tag">
          {{ tag !== "" && tag }}
        </li>
      </ul>
      <div class="container code-location-container">
        <span class="short-code">{{ truck.shortCode }}</span>
        <span class="location">{{ truck.location }}</span>
      </div>
      <div class="price-container">
        <p class="container ask-price">
          <span>Ask Price</span>
          <span>{{ formatPrice(truck.askPrice) }} &euro;</span>
        </p>
        <p class="container">
          <span>Current Offer</span>
          <span>{{ formatPrice(truck.highestBid) }} &euro;</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["truck"],
  methods: {
    formatPrice(price) {
      if (price === "") return "-";
      else if (price >= 1000) return (price / 1000).toFixed(3);
      else return price;
    },
  },
};
</script>


<style scoped>
img {
  width: 100%;
  height: 262px;
  border-radius: 5px 5px 0 0;
  object-fit: contain;
}

h2 {
  padding: 0 1rem;
  margin: 0.5rem 0;
  height: 60px;
}

.truck-card {
  color: #33657e;
  width: 350px;
  height: 580px;
  margin: 1rem;
  border-radius: 5px;
  box-shadow: 1px 1px 15px 2px rgba(0, 0, 0, 0.15);
  font-weight: 600;
}

.tag-list {
  display: flex;
  flex-wrap: wrap;
  align-items: flex-start;
  width: 90%;
  height: 80px;
  overflow: auto;
  padding: 1rem;
}

.tag {
  text-transform: uppercase;
  background-color: #ebf0f2;
  color: #0e3040;
  font-size: 0.8rem;
  font-weight: 800;
  box-sizing: border-box;
  padding: 0.4rem 0.8rem;
  margin: 0 0.3rem 0.3rem 0;
  border-radius: 5px;
}

.container {
  display: flex;
  justify-content: space-between;
  padding: 0 1rem;
}

.code-location-container {
  padding: 1rem;
}

.short-code {
  color: #d6e0e5;
}

.price-container {
  border-top: 3px solid #d6e0e5;
}

.ask-price {
  font-weight: 400;
  color: #82a1b0;
}
</style>