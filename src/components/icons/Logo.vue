<script setup>
import Image from "@/components/elements/Image.vue";
defineProps(
    {
      width: {
        type: Number,
        default: 32,
        required: false
      },
      height: {
        type: Number,
        default: 40,
        required: false
      }
    }
)
</script>
<template>
  <div class="logo">
    <Image
        src="/src/assets/logo.svg"
        :height="height"
        :width="width"
        alt="Visualsoft Logo"
    />
  </div>
</template>
