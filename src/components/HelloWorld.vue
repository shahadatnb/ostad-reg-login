<template>
  <div>
    <h2>List of Items</h2>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <strong>Name:</strong> {{ item.name }} <strong>Age:</strong> {{ item.age }}
      </li>
    </ul>
  </div>
</template>

<script setup>
  const items = [
        { name: 'John', age: 25 },
        { name: 'Jane', age: 30 },
        { name: 'Bob', age: 40 },
      ]
</script>
