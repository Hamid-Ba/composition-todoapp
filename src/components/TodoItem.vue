<template>
  <li class="card" draggable="true">
        <div class="cb-container">
          <input @click="ChangeStatus(props.todo.id)" :checked="props.todo.isCompleted" type="checkbox" class="cb-input" />
          <span class="check"></span>
        </div>
        <p class="item" v-text="props.todo.title"></p>
        <button class="clear" @click="DeleteItem(props.todo.id)">
          <img src="../assets/icon-cross.svg" alt="Clear it" />
        </button>
      </li>
</template>

<script setup>
import {defineProps , defineEmits} from "vue";

const props = defineProps({
  todo : Object
})

const emits = defineEmits(['StatusChanged','ItemDeleted'])

let ChangeStatus = (id) =>{
  emits('StatusChanged',id)
}

let DeleteItem = (id) =>{
  if(confirm("Are U Sure About That ?"))
    emits('ItemDeleted',id)
}

</script>
