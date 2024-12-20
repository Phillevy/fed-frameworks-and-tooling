<script setup>
import Navigation from '@/components/Navigation.vue'

const SecondaryMenuName = 'secondary-nav';
const SecondaryMenuNav = [
  {url: '#', title: 'All', className: 'selected'},
  {url: '#', title: 'Groups'},
  {url: '#', title: 'Segments'}
];
</script>

<template>
  <div class="filters">
    <div class="container m-auto">
      <div class="w-full flex flex-nowrap">
        <div class="content-end w-auto">
          <Navigation
              :class-name="SecondaryMenuName"
              :navigation="SecondaryMenuNav"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style>
  .filters
  {
    background-color: #040138;
    color: #FFFFFF;
  }
</style>