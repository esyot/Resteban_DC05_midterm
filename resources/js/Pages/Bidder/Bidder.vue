<script>
import Layout from "@/Layouts/Layout.vue";
export default {
  layout: Layout,
  props: {
    bidders: Array,
  },
  data() {
    return {
      searchValue: "",
      filteredBidders: this.bidders,
    };
  },
  methods: {
    searchCar(value) {
      this.filteredBidders = this.bidders.filter((bidder) => {
        return (
          bidder.first_name.toLowerCase().includes(value.toLowerCase()) ||
          bidder.last_name.toLowerCase().includes(value.toLowerCase())
        );
      });
    },
  },
};
</script>

<template>
  <div>
    <input
      type="text"
      placeholder="Search a bidder"
      v-model="searchValue"
      @input="searchCar(searchValue)"
    />
  </div>

  <section>
    <div class="card" v-for="bidder in filteredBidders" :key="bidder.id">
      <span>Name: {{ bidder.last_name }}, {{ bidder.first_name }}</span>
      <span>Address: {{ bidder.address }}</span>
      <span>Email: {{ bidder.email }}</span>
    </div>
  </section>
</template>

<style>
section {
  display: flex;
  flex-wrap: wrap;
  height: 80vh;
  overflow-y: auto;
}

section .card {
  background-color: #fff;
  padding: 10px;
}
</style>
