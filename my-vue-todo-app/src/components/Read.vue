<template>
  <!-- Read Item Operation -->
  <!-- Responsible for displaying the list of items and providing options to edit or delete each item  -->
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <input type="checkbox" />
        <input type="text" :value="item" class="todo-input" />
        <!-- {{ item }} -->
        <button @click="editItem(index)" class="pen-btn">
          <i class="fa-solid fa-pen" style="color: #454545"></i>
        </button>

        <button @click="deleteItem(index)" class="trash-btn">
          <i class="fa-solid fa-trash" style="color: #3f4040"></i>
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Read",

  props: {
    // Receive items array from parent component
    items: Array,
  },
  methods: {
    // This emits an "edit" event with the index of the item to edit
    editItem(index) {
      this.$emit("edit", index);
    },
    deleteItem(index) {
      this.$emit("delete", index);
    },
  },
};
</script>

<style scoped>
ul > li {
  list-style: none;
}

ul {
  border-radius: 0.3em;
  padding-top: 0.3em;
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1),
    0 8px 10px -6px rgb(0 0 0 / 0.1);
}

li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1em;
  width: 100%;
  padding: 0.5rem;
  border-radius: 0.2rem;
  background-color: #fff;
  border-bottom: 1px solid #ccc;
}

.todo-input {
  width: 100%;
  border: none;
  outline: none;
  font-size: 1rem;
  font-weight: 500;
  color: #333;
}

/* FOR LINE THROUGH */
input[type="checkbox"]:checked + input[type="text"] {
  color: #ccc;
  text-decoration: line-through;
}

button {
  background: transparent;
  border: none;
}

.pen-btn:hover,
.trash-btn:hover {
  cursor: pointer;
}
</style>
