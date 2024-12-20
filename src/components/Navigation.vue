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
        class="menu"
        :list="navigation"
    />
  </nav>
</template>

<style>
.menu
{
  margin: 1rem 0;
  padding: 0 0 1rem 0;
  list-style: none;
}

.menu li
{
  display: block;
  margin: 0;
  list-style: none;
  width: 100%;
}

.menu li a
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

.menu li.selected a
{
  border-bottom: 0.3rem solid #029FB4;
}

.menu li:hover a
{
  color: #1EAEDB;
}

@media (min-width: 576px)
{
  .menu
  {
    margin: 0;
    padding: 0;
  }

  .menu li
  {
    display: inline-block;
    width: auto;
  }

  .menu li a
  {
    padding: 1rem 1rem 1.3rem 1rem;
    border-bottom: none;
  }

  .menu li.selected a
  {
    padding-bottom: 1rem;
  }
}
</style>