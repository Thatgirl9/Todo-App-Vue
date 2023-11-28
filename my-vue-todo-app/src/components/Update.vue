<template>
  <!-- Update Operation -->
  <!-- Responsible for editing an existing item -->
  <div class="update-div">
    <form @submit.prevent="updateItem">
      <label for="itemName">
        <button class="icon-btn">
          <i class="fa-solid fa-pen" style="color: #fff"></i>
        </button>
        <input
          type="text"
          v-model="updatedItemName"
          placeholder="Edit..."
          required
          class="todo-input"
        />
        <button type="submit" class="edit-btn">Edit</button>
      </label>
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
      // Emit an "update" event with the updated item name to the parent component when the form is submitted.
      this.$emit("update", this.updatedItemName);
      this.updatedItemName = "";
    },
  },
};
</script>

<style scoped>
.update-div {
  width: 100%;
  margin-top: 1.2rem;
}

label {
  background-color: black;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1em;
  width: 100%;
  padding: 0.5rem;
  border-radius: 0.2rem;
}

.icon-btn {
  background-color: transparent;
  border: none;
}

.todo-input {
  width: 100%;
  border: none;
  outline: none;
  font-size: 1rem;
  font-weight: 500;
  color: #fff;
  background: transparent;
}

.todo-input::placeholder {
  color: #ccc;
}

.edit-btn {
  background-color: white;
  border: none;
  color: black;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  border: 1px solid #fff;
  padding: 0 0.5rem;
  border-radius: 0.2em;
}
</style>
