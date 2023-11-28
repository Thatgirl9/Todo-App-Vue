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
    updateItem(updatedItemName) {
      this.items[this.selectedItemIndex] = updatedItemName;
      this.isEditing = false;
      this.selectedItemIndex = null;
    },
    startDelete(index) {
      this.isDeleting = true;
      this.selectedItemIndex = index;
    },
    deleteItem() {
      this.items.splice(this.selectedItemIndex, 1);
      this.isDeleting = false;
      this.selectedItemIndex = null;
    },
    cancelDelete() {
      this.isDeleting = false;
      this.selectedItemIndex = null;
    },
  },
};
</script>

<template>
  <div class="main-container">
    <div class="black-con"></div>
    <div class="todo-main-con">
      <div class="todo-con">
        <div class="img-header">
          <h1 class="todo-header">Todo App</h1>
          <img src="./assets/icons8-checklist-53.png" />
        </div>

        <div class="todo-list-con">
          <Create @add="addItem"></Create>
          <Read :items="items" @edit="editItem" @delete="startDelete"> </Read>
          <Update v-if="isEditing" @update="updateItem"></Update>
          <Delete
            v-if="isDeleting"
            @confirm="deleteItem"
            @cancel="cancelDelete"
          ></Delete>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@400;500;600;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Josefin Sans", sans-serif;
}

.main-container {
  width: 100%;
  height: 100vh;
  /* color: white; */
}

.black-con {
  background-color: black;
  width: 100%;
  height: 40vh;
}
.todo-main-con {
  display: flex;
  justify-content: center;
  align-items: center;
  /* border: 2px solid red; */
  flex-direction: column;
  margin-top: -10em;
}

.todo-con {
  /* padding: 0.4em 2em; */
  /* border: 2px solid green; */
  width: 30%;
}

.img-header {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: space-between;
  margin-bottom: 2em;
  /* border: 1px solid blue; */
}
.todo-header {
  font-family: "Josefin Sans", sans-serif;
  /* font-size: 3em; */
  font-weight: 600;
  color: white;
}
.todo-list-con {
  /* border: 2px solid purple; */
}

@media screen and (max-width: 768px) {
  .todo-con {
    width: 95%;
  }
}
</style>
