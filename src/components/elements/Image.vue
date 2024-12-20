<script setup>
defineProps(
    {
      src: {
        type: String,
        required: true
      },
      width: {
        type: Number,
        required: false
      },
      height: {
        type: Number,
        required: false
      },
      alt: {
        type: String,
        required: false
      },
      className: {
        type: String,
        required: false
      }
    }
)
</script>

<template>
  <img
      :src="src"
      :height="height"
      :width="width"
      :alt="alt"
      :class="className"
  >
</template>
