<template>
  <div>
    <h2>Delete Item</h2>
    <p>Are you sure you want to delete this item?</p>
    <button @click="confirmDelete">Yes</button>
    <button @click="cancelDelete">No</button>
  </div>
</template>

<script>
export default {
  name: "Delete",
  methods: {
    confirmDelete() {
      this.$emit("confirm");
    },
    cancelDelete() {
      this.$emit("cancel");
    },
  },
};
</script>

<style scoped></style>
