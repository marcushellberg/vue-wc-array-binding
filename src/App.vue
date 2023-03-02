<script setup lang="ts">
import { ref } from "vue";
import "@vaadin/grid";

type Customer = {
  id: number;
  name: string;
};

const data: Customer[] = [
  { id: 1, name: "Foo" },
  { id: 2, name: "Bar" },
];
const customers = ref(data);

// Update the state after 2 seconds
// The unordered list updates, the grid does not (unless you provide a new array)
setTimeout(() => customers.value.push({ id: 3, name: "Baz" }), 2000);
</script>

<template>
  <div class="container">
    <vaadin-grid :items="customers">
      <vaadin-grid-column path="id"></vaadin-grid-column>
      <vaadin-grid-column path="name"></vaadin-grid-column>
    </vaadin-grid>

    <ul>
      <li v-for="customer in customers">{{ customer.name }}</li>
    </ul>
  </div>
</template>

<style scoped>
.container {
  max-width: 500px;
  padding: 20px;
}
</style>
