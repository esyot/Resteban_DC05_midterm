<template>
  <header>
    <ul>
      <li @click="redirectTo('/')"><span>Home</span></li>
      <li @click="redirectTo('/cars')"><span>Cars</span></li>
      <li @click="redirectTo('/bidders')"><span>Bidders</span></li>
    </ul>
  </header>

  <slot></slot>
</template>

<script>
import { Inertia } from "@inertiajs/inertia";

export default {
  name: "Layout",

  methods: {
    redirectTo(link) {
      Inertia.visit(link, { method: "get", preserveState: true });
    },
  },
};
</script>

<style scoped>
header {
  background-color: rgb(82, 157, 255);
}
header ul {
  display: flex;
  gap: 3rem;
  list-style-type: none;
}
header li {
  padding: 10px;
  color: #fff;
}

header li:hover {
  background-color: #2461bb;
  cursor: pointer;
}

.link {
  text-decoration: none;
  color: #000;
}
</style>
