<template>
  <Header />
  <main>
    <TodoAdd @ItemAdded="AddTodo"/>
    <ul class="todos">

      <TodoItem v-for="(item,index) in todoList" :key="index" :todo="item"/>
      
    </ul>
    <div class="card stat">
      <p class="corner"><span id="items-left">0</span> مورد باقی مانده</p>
      <div class="filter">
        <button id="all" class="on">همه</button>
        <button id="active" >فعال</button>
        <button id="completed">تکمیل</button>
      </div>
      <div class="corner">
        <button id="clear-completed">حذف تکمیل شده ها</button>
      </div>
    </div>
  </main>
  <AppFooter />
</template>

<script setup>
import Header from './components/AppHeader.vue'
import TodoAdd from './components/TodoAdd.vue'
import TodoItem from './components/TodoItem.vue'
import AppFooter from './components/AppFooter.vue'
import { reactive } from 'vue'

var todoList = reactive([])

function AddTodo(todoTitle){
  const todoId = Math.random().toString(15).slice(3);
  var todo = {id:todoId,title : todoTitle,isCompleted : false}
  todoList.push(todo)
}

</script>
