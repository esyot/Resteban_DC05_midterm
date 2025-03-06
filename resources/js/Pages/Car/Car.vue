<script>
import Layout from "@/Layouts/Layout.vue";
export default {
  layout: Layout,
  props: {
    cars: Array,
  },
  data() {
    return {
      searchValue: "",
      filteredCars: this.cars,
    };
  },
  methods: {
    searchCar(value) {
      this.filteredCars = this.cars.filter((car) => {
        return (
          car.make.toLowerCase().includes(value.toLowerCase()) ||
          car.model.toLowerCase().includes(value.toLowerCase())
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
      placeholder="Search a car"
      v-model="searchValue"
      @input="searchCar(searchValue)"
    />
  </div>

  <section>
    <div class="card" v-for="car in filteredCars" :key="car.id">
      <span>Factory: {{ car.make }}</span>
      <span>Model: {{ car.model }}</span>
      <span>Miles: {{ car.miles }}</span>
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
