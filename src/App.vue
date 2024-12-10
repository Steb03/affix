<script setup>
import { ref, watch } from 'vue';
import Navbar from '@/components/Navbar.vue'

let theme = ref('light');

let addTodo = ref('');

watch(theme, (newTheme) => {
  if (newTheme === 'dark') {
    document.body.classList.add('dark');
    document.body.classList.remove('light');
  } else {
    document.body.classList.add('light');
    document.body.classList.remove('dark');
  }
});
</script>

<template>
  <Navbar @theme="(t) => theme = t " />
  <div id="list-div" :class="theme">
    <h1 :class="theme">Start your journey with a task...</h1>
    <div id="h2-underline"></div>
    <div id="input-div">
      <input type="text" id="addTaskInput" placeholder="Add something to your day..." v-model="addTodo" />
      <button id="submitButton">+</button>
    </div>
  </div>
</template>

<script>
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Archivo+Narrow&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
@import '/src/assets/base.css';

body {
  transition: 0.2s ease all, left 0.2s cubic-bezier(0.18, 0.89, 0.35, 1.15);
  font-family: Poppins, Archivo Narrow, sans-serif;
}

body.dark {
  background-color: var(--dark-bg);
}

div #list-div {
  width: 70vw;
  height: 20vh;
  position: absolute;
  top: 150px;
  left: 15vw;
  border-radius: 4px;  
  border-style: solid;
  border-width: 1px;
  transition: 0.2s ease all, left 0.2s cubic-bezier(0.18, 0.89, 0.35, 1.15);
}

#list-div.dark {
  background-color: #242424;
  border-color: var(--border-color-dark);
}

h1 {
  font-weight: 400;
  text-align: center;
  margin-top: 20px;
  font-size: 2.5em !important;
}

h1.dark {
  color: var(--dark-mode-text-color);
}

div #h2-underline {
  width: 30vw;
  height: 3px;
  border-radius: 2px;
  background-color: var(--theme-blue-green);
  position: absolute;
  left: 20vw;
  top: calc(50px + 2.5em);
}

#input-div {
  display: inline;
  position:absolute;
  left: calc((70vw - 600px) / 2);
  width: 600px;
  height: 45px;
  border-style: solid;
  border-width: 1px;
  border-radius: 4px;

}

#addTaskInput {
  width: 542px;
  border: none;
  height: 43px;
  position: absolute;
  top: 0;
  left: 0;
  border-radius: 4px;
  font-size: 1em;
}

#submitButton {
  width: 50px;
}
</style>