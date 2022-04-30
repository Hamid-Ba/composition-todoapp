<template>
   <header class="card">

     <h1>لیست وظایف </h1>
    
     <button id="theme-switcher" @click="changeTheme">
         <img :src="currentIcon" alt="Change color theme" />
     </button>
 </header>
</template>

<script setup>
import {ref} from "vue";
import SunIcon from '../assets/icon-sun.svg'
import MoonIcon from '../assets/icon-moon.svg'

var currentIcon = ref(SunIcon) 

function changeTheme(){
     if(currentIcon.value == SunIcon){
         currentIcon.value = MoonIcon
         document.querySelector('body').classList.add('light');
     }
     else{
         currentIcon.value = SunIcon
         document.querySelector('body').classList.remove('light');
     } 
}
</script>