<script setup>
import Image from "@/components/elements/Image.vue";
defineProps(
    {
      width: {
        type: Number,
        default: 90,
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
        src="/src/assets/logo_beta.svg"
        :height="height"
        :width="width"
        alt="Visualsoft Beta Logo"
    />
  </div>
</template>
