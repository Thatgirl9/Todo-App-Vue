<template>
  <div>
    <h2>Update Item</h2>
    <form @submit.prevent="updateItem">
      <label for="itemName">New Item Name:</label>
      <input type="text" v-model="updatedItemName" required />
      <button type="submit">Update Item</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Update",
  data() {
    return {
      updatedItemName: "",
    };
  },

  methods: {
    updateItem() {
      this.$emit("update", this.updatedItemName);
      this.updatedItemName = "";
    },
  },
};
</script>

<style scoped></style>
