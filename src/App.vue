<template>
  <Header />
  <main>
    <TodoAdd @ItemAdded="AddTodo"/>
    <ul class="todos">

      <TodoItem v-for="(item,index) in FilterByTabs" 
      :key="item.id" 
      :todo="item"
      @StatusChanged="ChangeStatus"
      @ItemDeleted="DeleteItem"
      @dragover.prevent
      @dragstart="DragStarted(index)"
      @drop="DropStarted(index)"/>
      
    </ul>
    <div class="card stat">
      <p class="corner"><span id="items-left">{{FilterByTabs.length}}</span> مورد </p>
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
import { ref ,computed} from 'vue'

var todoList = ref([])
var dragIndex = ref(-1)
var selectedTab = ref('all')

let AddTodo = (todoTitle) => {
  const todoId = Math.random().toString(15).slice(3);
  var todo = {id:todoId,title : todoTitle,isCompleted : false}
  todoList.value.push(todo)
}

let ChangeStatus = (itemId) => {
  var item = todoList.value.find(i => i.id == itemId);
  item.isCompleted = !item.isCompleted;
}

let DeleteItem = (itemId) => {
  var todos = [...todoList.value]
  todos = todos.filter(i => i.id !== itemId)
  todoList.value = todos
}

let DragStarted = (index) => {
  dragIndex.value = index;
}

let DropStarted = (index) => {
  var item = todoList.value.splice(dragIndex.value,1)[0];
  todoList.value.splice(index,0,item);
}

let ChangeTab = (tab) =>{
  selectedTab.value = tab;
}

let FilterByTabs = computed(() => {
  switch(selectedTab.value){
    case "active":
      return todoList.value.filter(t => !t.isCompleted)
    case "completed":
      return todoList.value.filter(t => t.isCompleted)
    default :
      return todoList.value;
  }
})

</script>
