<template>
  <form>
    <input
      type="text"
      v-model="searchText"
      placeholder="type to search"
      @input="filterList"
    />
    <div>
      <label for="sort">Sort</label>
      <select name="sort" id="sort" @change="sortList">
        <option value="date">Publishing Date</option>
        <option value="priceAsc">Price Ascending</option>
        <option value="priceDesc">Price Descending</option>
      </select>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    filterList() {
      this.$emit("filter-list", this.searchText);
    },
    sortList(e) {
      this.$emit("sort-list", e.target.value);
    },
  },
};
</script>

<style  scoped>
form {
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-sizing: border-box;
  height: 100px;
  width: 100%;
  padding: 0 2rem;
}

input,
select {
  height: 35px;
  padding: 0 0.5rem;
  border-radius: 6px;
  color: #002334;
  font-size: 1rem;
  font-weight: 600;
  transition: 0.2s ease-in-out;
}

option,
label {
  font-size: 1rem;
  font-weight: 600;
  padding: 1rem;
}

input {
  min-width: 300px;
  width: 35%;
  background-color: #e5e9ea;
  border: 1px solid #002334;
  outline: none;
}

select:hover {
  background-color: #002334;
  color: white;
}

select:focus {
  background-color: #e5e9ea;
  color: #002334;
}
</style>