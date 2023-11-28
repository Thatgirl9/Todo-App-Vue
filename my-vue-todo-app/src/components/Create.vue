<script>
export default {
  name: "Create",
  data() {
    return {
      newItemName: "",
    };
  },

  methods: {
    addItem() {
      this.$emit("add", this.newItemName);
      this.newItemName = "";
    },
  },
};
</script>

<!-- Create Todo Operation -->
<template>
  <div>
    <h2>Create Item</h2>
    <form>
      <label for="itemName">Item Name:</label>
      <input type="text" required v-model="newItemName" />
      <button type="submit">Add Item</button>
    </form>
  </div>
</template>

<style scoped></style>
