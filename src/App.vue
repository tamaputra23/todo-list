<template>
  <div id="app">
    <ToDoList />
  </div>
</template>

<script>
import ToDoList from './components/TodoComponent.vue'

export default {
  name: 'App',
  components: {
    ToDoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
.todo-list {
  margin: 20px auto;
  max-width: 600px;
  padding: 20px;
  border: 1px solid #39af39;
  box-shadow: 0px 0px 10px 0.5px #a1a1a1;
  border-radius: 5px;
}

.filters {
  margin-bottom: 10px;
}

.items {
  list-style: none;
  margin: 0;
  padding: 0;
}

.items li {
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

.item-text {
  flex-grow: 1;
  margin-left: 10px;
}

.completed {
  text-decoration: line-through;
}

.update-btn {
  margin-left: 10px;
}
.delete-btn {
  margin-left: 10px;
}

.add-item-form {
  display: flex;
  margin-top: 20px;
}

.add-item-form input[type="text"] {
  flex-grow: 1;
  padding: 5px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
}
.input[type="text"] {
  flex-grow: 1;
  padding: 5px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
}
.add-btn {
  padding: 5px;
  border: none;
  border-radius: 5px;
  background-color: #4CAF50;
  color: #fff;
  cursor: pointer;
  font-size: 16px;
  margin-left: 10px;
}

.update-btn {
  padding: 5px;
  border: none;
  border-radius: 5px;
  background-color: #acca17;
  color: #fff;
  cursor: pointer;
  font-size: 10px;
  margin-left: 10px;
}
.delete-btn {
  padding: 5px;
  border: none;
  border-radius: 5px;
  background-color: #b14040;
  color: #fff;
  cursor: pointer;
  font-size: 10px;
  margin-left: 10px;
}
.save-btn {
  padding: 5px;
  border: none;
  border-radius: 5px;
  background-color: #acca17;
  color: #fff;
  cursor: pointer;
  font-size: 10px;
  margin-left: 10px;
}
.cancel-btn {
  padding: 5px;
  border: none;
  border-radius: 5px;
  background-color: #b14040;
  color: #fff;
  cursor: pointer;
  font-size: 10px;
  margin-left: 10px;
}
</style>