<script setup>
defineProps(
    {
      title: {
        type: String,
        required: true
      },
      className: {
        type: String,
        required: false
      }
    }
)
</script>

<template>
  <h1 :class="className">
    {{ title }}
  </h1>
</template>
