<template>
    <div class="todo-list">
      <h2>Today ToDo</h2>
  
        <div class="filters">
            <label>
                <input type="radio" v-model="filter" value="all">
                All
            </label>
            <label>
                <input type="radio" v-model="filter" value="completed">
                Completed
            </label>
            <label>
                <input type="radio" v-model="filter" value="incomplete">
                Incomplete
            </label>
        </div>
        <input type="text" v-model="searchText" placeholder="Search ToDo">
        <transition name="fade">
            <ul class="items">
                <li v-for="item in filteredItems" :key="item.id">
                <input type="checkbox" v-model="item.completed">
                <span class="item-text" :class="{ completed: item.completed }">{{ item.text }}</span>
                <button class="update-btn" @click="showEditDialog(item)">Update</button>
                <button class="delete-btn" @click="removeItem(item)">Delete</button>
                </li>
            </ul>
        </transition>   
        <div v-if="showDialog">
            <div class="edit-dialog">
                <!-- Edit dialog content and form go here -->
                <input v-model="editedText" />
                <button class="save-btn" @click="updateItemText()">Save</button>
                <button class="cancel-btn" @click="closeDialog">Cancel</button>
            </div>
        </div>  
        <form class="add-item-form" @submit.prevent="addItem">
            <input type="text" v-model="newItem" placeholder="Add a new item">
            <button class="add-btn">Add</button>
        </form>
    </div>
    
  </template>
  
<script>
export default {
    data() {
        return {
            items: [
                { id: 1, text: 'Learn Vue.js', completed: false },
                { id: 2, text: 'Build an app', completed: false },
                { id: 3, text: 'Deploy the app', completed: false },
            ],
            newItem: '',
            filter: 'all',
            showDialog: false,
            editedText: "",
            selectedItem: null,
            searchText: "",
        };
    },
    watch: {
        searchText: 'filterItems'
    },
    methods: {
        addItem() {
            if (this.newItem.trim()) {
                this.items.push({
                    id: this.items.length + 1,
                    text: this.newItem.trim(),
                    completed: false
                });
                this.newItem = '';
            }
        },
        removeItem(item) {
            const index = this.items.indexOf(item);
            this.items.splice(index, 1);
        },
        showEditDialog(item) {
            this.showDialog = true;
            this.editedText = item.text;
            this.selectedItem = item;
        },
        updateItemText() {
            if (this.selectedItem) {
                this.selectedItem.text = this.editedText;
                // Implement your update logic
                // item.text = this.editedText
                this.closeDialog();
            }
        },
        closeDialog() {
            this.showDialog = false;
            this.editedText = "";
            this.selectedItem = null;
        },
        filterItems() {
            const searchText = this.searchText.toLowerCase();

            switch (this.filter) {
            case 'completed':
                this.filteredItems = this.items.filter(item => item.completed || item.text.toLowerCase().includes(searchText));
                break;
            case 'incomplete':
                this.filteredItems = this.items.filter(item => !item.completed || item.text.toLowerCase().includes(searchText));
                break;
            default:
                this.filteredItems = this.items;
            }
        }
    },
    computed: {
        filteredItems() {
            const searchText = this.searchText.toLowerCase();
            switch (this.filter) {
                case 'completed':
                    return this.items.filter(item => item.completed && item.text.toLowerCase().includes(searchText));
                case 'incomplete':
                    return this.items.filter(item => !item.completed && item.text.toLowerCase().includes(searchText));
                default:
                    return this.items;
            }
        }
    }
};
</script>
<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
