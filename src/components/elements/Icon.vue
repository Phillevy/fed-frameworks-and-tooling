<script setup>
defineProps(
    {
      name: {
        type: String,
        required: false
      }
    }
)
</script>

<template>
  <i
      v-if="name"
      :class="'fa-solid fa-' + name"
  ></i>
</template>
