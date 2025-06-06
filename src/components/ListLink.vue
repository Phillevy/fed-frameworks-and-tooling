<script setup>
import Link from '@/components/elements/Link.vue'
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
  <li :class="className">
    <Link
        :href="href"
        :title="title"
        class-name="link"
    />
  </li>
</template>
