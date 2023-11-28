<template>
  <!-- Delete Operation -->
  <!-- Responsible for confirming or canceling the deletion of an item -->
  <div class="delete-div">
    <div class="del-div">
      <button class="trash-btn">
        <i class="fa-solid fa-trash" style="color: #fff"></i>
      </button>
      <p>Are you sure you want <br />to delete this item?</p>
      <button @click="confirmDelete" class="yes-btn">Yes</button>
      <button @click="cancelDelete">No</button>
    </div>
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

<style scoped>
.delete-div {
  margin-top: 1.2rem;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.del-div {
  display: flex;
  flex-direction: column;
  gap: 1em;
  background: black;
  padding: 0.5em;
  border-radius: 6px;
}

.trash-btn {
  background: transparent;
  border: none;
}

button:hover {
  cursor: pointer;
}
</style>
