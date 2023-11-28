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
  <div class="create-div">
    <!-- <h2>Create Item</h2> -->
    <form>
      <label for="itemName" class="write-todo">
        <input type="checkbox" />
        <input
          type="text"
          required
          v-model="newItemName"
          class="todo-input"
          placeholder="Create a new todo..."
        />
        <button class="icon-tick" @click="addItem" type="submit">
          <i class="fa-solid fa-check tick" style="color: #4e4b4b"></i>
        </button>
      </label>

      <!-- <button type="submit" >Add Item</button> -->
    </form>
  </div>
</template>

<style scoped>
.create-div {
  width: 100%;
  margin-bottom: 1.2rem;
}
.write-todo {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1em;
  width: 100%;
  padding: 0.5rem;
  border-radius: 0.2rem;
  background-color: #fff;
  box-shadow: 0 0 0.5rem rgba(0, 0, 0, 0.2);
  margin-bottom: 1rem;
}

.todo-input {
  width: 100%;
  border: none;
  outline: none;
  font-size: 1rem;
  font-weight: 500;
  color: #333;
}

.icon-tick {
  width: 20px;
  height: 20px;
  background: transparent;
  border: none;
}

.tick {
  font-size: 1rem;
}

.icon-tick:hover {
  cursor: pointer;
}
</style>
