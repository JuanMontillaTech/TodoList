<script setup>
import { ref } from 'vue';
//Variables reactivas
const newTodo = ref('');
const todos = ref([]);
const addTodo = () => {
  todos.value.push(newTodo.value)
  newTodo.value = '';
}
const removeTodo = (idx) => {
  todos.value.splice(idx, 1);
}

</script>

<template>
  <div>
    <h1>Mis Tareas</h1>
    <div class="row g-3">
      <div class="col-auto">
        <input v-model="newTodo" id="tarea" placeholder="Agregar tarea" @keyup.enter="addTodo" />
      </div>
      <div class="col-auto">
        <button @click="addTodo" class="btn btn-primary" @keyup.enter="addTodo">Agregar</button>
      </div>
     </div>
    <ul class="list-group w-100">
      <li class="list-group-item" v-for="(todo, index) in todos">
        <div class="alert alert-secondary" role="alert">
          {{ todo }}
          <button class="btn btn-danger" @click="removeTodo(index)">X</button>
        </div> 
      </li>
    </ul>
  </div>
</template>

<style scoped></style>