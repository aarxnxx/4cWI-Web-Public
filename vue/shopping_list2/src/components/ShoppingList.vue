<template>
  <div id="app">
    <button @click="addFruit">Add fruit</button>
    <ul>
      <h2 v-for="(fruit, i) in fruits" :key="i">
        {{ fruit }}
      </h2>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fruits: ['Orange', 'Apple', 'Mango'],
    };
  },
  methods: {
    addFruit() {
      this.fruits.push('Banana');
    },
  },
};
</script>

<!-- <template>
  <header>
    <h1>Test</h1>
  </header>
  <p>Anzahl: {{ numberItem }}</p>
  <p>Kosten: {{ costsItem }}</p>
  <button @click="deleteItem">Delete</button>
</template>

<script>
export default {
  emits: ['delete'],
  data() {
    return {
      itemDeleted: false,
      numberItem: 0,
      costsItem: 0,
    };
  },

  methods: {
    deleteItem() {
      this.$emit('delete', this.id);
    },
  },
};
</script>

<style></style> -->
