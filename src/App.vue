<template>
  <router-link to="/">Login</router-link>
  &nbsp
  <router-link to="/todo">Todo</router-link>
  &nbsp
  <router-link to="/user">User</router-link>
  <router-view></router-view>
</template>

<script setup>
import Todo from './components/Todo.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>