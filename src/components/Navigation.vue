<script setup>
import Menu from '@/components/ListLinks.vue'
defineProps(
    {
      className: {
        type: String,
        required: false
      },
      navigation: {
        type: Array,
        required: true
      }
    }
)
</script>

<template>
  <nav :class="className">
    <Menu
        class="menu md:my-0 my-4 md:pb-0 pb-4 list-none"
        :list="navigation"
    />
  </nav>
</template>

<style scoped>

.menu :deep(li)
{
  @apply block;
  margin: 0;
  list-style: none;
  width: 100%;
}

.menu :deep(li a)
{
  margin: 0;
  display: inherit;
  padding: 0.5rem 0.5rem 0.25rem 0.5rem;
  text-decoration: none;
  color: inherit;
  vertical-align: bottom;
  box-sizing: border-box;
  width: auto;
  border-bottom: 1px solid #ccc;
}

.menu :deep(li.selected a)
{
  border-bottom: 0.3rem solid #029FB4;
}

.menu :deep(li:hover a)
{
  color: #1EAEDB;
}

@media (min-width: 775px)
{
  .menu :deep(li)
  {
    @apply inline-block;
    width: auto;
  }

  .menu :deep(li a)
  {
    padding: 1rem 1rem 1.3rem 1rem;
    border-bottom: none;
  }

  .menu :deep(li.selected a)
  {
    padding-bottom: 1rem;
  }
}
</style>