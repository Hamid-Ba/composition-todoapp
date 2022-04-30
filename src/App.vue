<template>
  <Header />
  <main>
    <TodoAdd @ItemAdded="AddTodo"/>
    <ul class="todos">

      <TodoItem v-for="(item,index) in todoList" 
      :key="index" 
      :todo="item"
      @dragover.prevent
      @dragstart="DragStarted(index)"
      @drop="DropStarted(index)"/>
      
    </ul>
    <div class="card stat">
      <p class="corner"><span id="items-left">0</span> مورد باقی مانده</p>
      <div class="filter">
        <button id="all" :class="{'on' : selectedTab == 'all'}" @click="ChangeTab('all')">همه</button>
        <button id="active" :class="{'on' : selectedTab == 'active'}" @click="ChangeTab('active')">فعال</button>
        <button id="completed" :class="{'on' : selectedTab == 'completed'}" @click="ChangeTab('completed')">تکمیل</button>
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
import { reactive, ref } from 'vue'

var todoList = reactive([])
var dragIndex = ref(-1)
var selectedTab = ref('all')

let AddTodo = (todoTitle) => {
  const todoId = Math.random().toString(15).slice(3);
  var todo = {id:todoId,title : todoTitle,isCompleted : false}
  todoList.push(todo)
}

let DragStarted = (index) => {
  dragIndex.value = index;
}

let DropStarted = (index) => {
  var item = todoList.splice(dragIndex.value,1)[0];
  todoList.splice(index,0,item);
}

let ChangeTab = (tab) =>{
  selectedTab.value = tab;
}

</script>
