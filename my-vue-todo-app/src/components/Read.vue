<template>
  <!-- Read Item Operation -->
  <div>
    <!-- <h2>Read Items</h2> -->
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <input type="checkbox" />
        <input type="text" :value="item" class="todo-input" />
        <!-- {{ item }} -->
        <button @click="editItem(index)" class="pen-btn">
          <i class="fa-solid fa-pen" style="color: #454545"></i>
        </button>
        <!-- <button @click="deleteItem(index)">Delete</button> -->
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

<style scoped>
ul > li {
  list-style: none;
}

ul {
  /* border: 2px solid red; */
  /* background-color: peru; */
  border-radius: 0.3em;
  padding-top: 0.3em;
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1),
    0 8px 10px -6px rgb(0 0 0 / 0.1);
}

li {
  /* border: 2px solid goldenrod; */
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1em;
  width: 100%;
  padding: 0.5rem;
  border-radius: 0.2rem;
  background-color: #fff;
  /* box-shadow: 0 0 0.5rem rgba(0, 0, 0, 0.2); */
  /* margin-bottom: 1rem; */
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

button {
  background: transparent;
  border: none;
}

.pen-btn:hover,
.trash-btn:hover {
  cursor: pointer;
}
</style>
