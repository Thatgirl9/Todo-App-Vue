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
      // Stores the list of items and variables
      items: [],
      // Manages the state of editing and deleting items
      isEditing: false,
      isDeleting: false,
      selectedItemIndex: null,
    };
  },

  // LOCAL STORAGE MOUNTED

  mounted() {
    this.loadItemsFromLocalStorage();
  },

  methods: {
    addItem(newItemName) {
      // Add the new item to the items array
      this.items.push(newItemName);

      // Save items to local storage
      this.saveItemsToLocalStorage();
    },
    editItem(index) {
      // Sets the state(isEditing = true) to start editing an item.
      this.isEditing = true;
      // Stores the index of the item being called
      this.selectedItemIndex = index;
    },

    updateItem(updatedItemName) {
      // Update the item at the selected index with the updated item name(new name)
      this.items[this.selectedItemIndex] = updatedItemName;
      this.isEditing = false;
      this.selectedItemIndex = null;

      // Save items to local storage after update
      this.saveItemsToLocalStorage();
    },

    startDelete(index) {
      // Sets the state(isDeleting = true) to start deleting an item and stores the index of the item being selected.
      this.isDeleting = true;
      this.selectedItemIndex = index;
    },

    deleteItem() {
      // Delete the item at the selected index
      this.items.splice(this.selectedItemIndex, 1);
      this.isDeleting = false;
      this.selectedItemIndex = null;

      // Save items to local storage after delete
      this.saveItemsToLocalStorage();
    },
    cancelDelete() {
      // Sets the state(isDeleting = false) to cancel deleting an item.
      this.isDeleting = false;
      this.selectedItemIndex = null;
    },

    saveItemsToLocalStorage() {
      // Save items array to local storage
      localStorage.setItem("todoItems", JSON.stringify(this.items));
    },

    loadItemsFromLocalStorage() {
      // Load items from local storage
      const storedItems = localStorage.getItem("todoItems");
      if (storedItems) {
        this.items = JSON.parse(storedItems);
      }
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
          <h1 class="todo-header">To-do App</h1>
          <img src="./assets/icons8-checklist-53.png" />
        </div>

        <div class="todo-list-con">
          <Create @add="addItem"></Create>
          <Read :items="items" @edit="editItem" @delete="startDelete"> </Read>
          <!-- V-if(conditional rendering) shows the update and delete components based on their state(True/false) - (isEditing and isDeleting) -->
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
  flex-direction: column;
  margin-top: -10em;
}

.todo-con {
  width: 30%;
}

.img-header {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: space-between;
  margin-bottom: 2em;
}
.todo-header {
  font-family: "Josefin Sans", sans-serif;
  font-weight: 600;
  color: white;
}

@media screen and (max-width: 768px) {
  .todo-con {
    width: 95%;
  }
}
</style>
