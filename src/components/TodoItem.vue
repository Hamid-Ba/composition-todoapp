<template>
  <li class="card" draggable="true">
        <div class="cb-container">
          <input :checked="props.todo.isCompleted" type="checkbox" class="cb-input" />
          <span class="check"></span>
        </div>
        <p class="item" v-text="props.todo.title"></p>
        <button class="clear">
          <img src="../assets/icon-cross.svg" alt="Clear it" />
        </button>
      </li>
</template>

<script setup>
import {defineProps} from "vue";

const props = defineProps({
  todo : Object
})

</script>
