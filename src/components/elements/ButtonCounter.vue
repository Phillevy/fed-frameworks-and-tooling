<script setup>
import Icon from '@/components/elements/Button.vue'
import Button from "@/components/elements/Button.vue";
defineProps(
    {
      title: {
        type: String,
        required: true
      },
      subtitle: {
        type: String,
        required: true
      },
      id: {
        type: String,
        required: false
      },
      className: {
        type: String,
        required: false
      },
      icon: {
        type: String,
        required: false
      }
    }
)
</script>

<template>
  <div>
    <Button
        class="button"
        :title="title"
        :class="className"
        :id="id"
    />
    <sup>{{ subtitle }}</sup>
  </div>
</template>

<style scoped>
div {
  display: inline-block;
  position: relative;
}
div :deep(button span) {
  font-weight: bold;
}
sup {
  position: absolute;
  top: -0.6rem;
  right: -0.6rem;
  background-color: #040138;
  color: #fff;
  border-radius: 50%;
  height: 1.2rem;
  width: 1.2rem;
  font-size: 0.8rem;
  line-height: 1.2rem;
  font-weight: normal;
  text-align: center;
}
</style>