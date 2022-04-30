<template>
  <div class="card add">
      <div class="cb-container">
        <button id="add-btn" @click="AddItem">+</button>
      </div>
      <div class="txt-container">
        <label for="addt">افزودن </label>
        <input v-model="title" type="text" class="txt-input"
          placeholder="افزودن وظیفه جدید..." 
          spellcheck="false" 
          autocomplete="off"
          id="addt" 
          dir="rtl"
          @keypress.enter="AddItem" />
      </div>
    </div>
</template>

<script setup>
import {ref , defineEmits} from 'vue'

var title = ref("");
const emits = defineEmits(["ItemAdded"])

function AddItem(){
  if(!title.value) return;
  emits("ItemAdded",title.value)
  title.value = ""
}

</script>
