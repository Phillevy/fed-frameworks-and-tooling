<script setup>
defineProps(
    {
      href: {
        type: String,
        required: true
      },
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
  <a
      :href="href"
      :class="className"
  >
    {{ title }}
  </a>
</template>
