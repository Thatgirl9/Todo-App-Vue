<script>
import Create from "./components/Create.vue";
import Delete from "./components/Delete.vue";
import Read from "./components/Read.vue";
import Update from "./components/Update.vue";

export default {
  name: "App",
  components: {
    Create,
    Read,
    Update,
    Delete,
  },
  data() {
    return {
      items: [],
      isEditing: false,
      isDeleting: false,
      selectedItemIndex: null,
    };
  },

  methods: {
    addItem(newItemName) {
      this.items.push(newItemName);
    },
    editItem(index) {
      this.isEditing = true;
      this.selectedItemIndex = index;
    },
  },
};
</script>

<template>
  <div>
    <h1>My Vue Todo App</h1>
    <Create />
    <Read />
    <Update />
    <Delete />
  </div>
</template>

<style scoped></style>
