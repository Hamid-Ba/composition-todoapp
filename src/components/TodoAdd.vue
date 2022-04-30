<template>
  <div class="card add">
      <div class="cb-container">
        <button id="add-btn" @click="AddItem()">+</button>
      </div>
      <div class="txt-container">
        <label for="addt">افزودن </label>
        <input v-model="item.title" type="text" class="txt-input" placeholder="افزودن وظیفه جدید..." spellcheck="false" autocomplete="off"
          id="addt" dir="rtl" />
      </div>
    </div>
</template>

<script setup>
import {reactive , defineEmits} from 'vue'

var item = reactive({id:"",title:"",isCompleted:false});
const emits = defineEmits(["ItemAdded"])

function AddItem(){
  if(!item.title) return;
  item.id = Math.random().toString(15).slice(3);
  emits("ItemAdded",item)
}

</script>
