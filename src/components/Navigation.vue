<script setup>
defineProps([
  'navigation'
])
</script>

<template>
  <nav class="top-nav">
    <h4>{{ navigation }}</h4>
    <ul class="menu">
      <li  v-for="todo in navigation" class="selected"><a href="#">{{ todo.title }}</a></li>
      <li><a href="#">Reviews</a></li>
      <li><a href="#">Requests</a></li>
      <li><a href="#">Appointments</a></li>
    </ul>
  </nav>
</template>
