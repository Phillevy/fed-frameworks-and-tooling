<script setup>
import ListLink from '@/components/ListLink.vue'
defineProps(
    {
      className: {
        type: String,
        required: false
      },
      list: {
        type: Array,
        required: true
      }
    }
)
</script>

<template>
  <ul :class="className">
    <ListLink
        v-for="link in list"
        :href="link.url"
        :title="link.title"
        :class-name="link.className"
    />
  </ul>
</template>
