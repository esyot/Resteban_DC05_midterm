<template>
  <header>
    <ul>
      <Link :href="'/'" class="link">
        <li><span>Home</span></li>
      </Link>
      <Link :href="'/cars'" class="link">
        <li><span>Cars</span></li>
      </Link>
      <Link :href="'/bidders'" class="link">
        <li><span>Bidders</span></li>
      </Link>
      <Link :href="'/biddings'" class="link">
        <li><span>Biddings</span></li>
      </Link>
    </ul>
  </header>

  <slot></slot>
</template>

<script>
import { Link } from "@inertiajs/inertia-vue3";

export default {
  name: "Layout",
  components: {
    Link,
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
