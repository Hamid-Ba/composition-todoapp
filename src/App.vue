<template>
  <Header />
  <main>
    <TodoAdd />
    <ul class="todos">

      <TodoItem />
      
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


</script>
