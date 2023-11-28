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

  // LOCAL STORAGE MOUNTED

  mounted() {
    //   if(localStorage.getItem('items')){
    //     try{
    //       this.items = JSON.parse(localStorage.getItem('items'));
    //     } catch(e){
    //       localStorage.removeItem('items');
    //     }
    //   }
    // },
    // Load items from local storage when the component is created.
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
      this.isEditing = true;
      this.selectedItemIndex = index;
    },
    updateItem(updatedItemName) {
      this.items[this.selectedItemIndex] = updatedItemName;
      this.isEditing = false;
      this.selectedItemIndex = null;

      // Save items to local storage after update
      this.saveItemsToLocalStorage();
    },
    startDelete(index) {
      this.isDeleting = true;
      this.selectedItemIndex = index;
    },
    deleteItem() {
      this.items.splice(this.selectedItemIndex, 1);
      this.isDeleting = false;
      this.selectedItemIndex = null;

      // Save items to local storage after delete
      this.saveItemsToLocalStorage();
    },
    cancelDelete() {
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
