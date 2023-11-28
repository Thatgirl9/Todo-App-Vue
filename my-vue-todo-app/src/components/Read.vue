<template>
  <!-- Read Item Operation -->
  <div>
    <h2>Read Items</h2>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ item }}
        <button @click="editItem(index)">Edit</button>
        <button @click="deleteItem(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Read",

  props: {
    // items: {
    //   type: Array,
    //   required: true,
    // },
    items: Array,
  },
  methods: {
    editItem(index) {
      this.$emit("edit", index);
    },
    deleteItem(index) {
      this.$emit("delete", index);
    },
  },
};
</script>

<style scoped></style>
