<script setup>
import Logo from './Logo.vue'
import Inventory from './Inventory.vue'
import Navigation from './Navigation.vue'
</script>

<template>
  <div class="header">
    <div class="container m-auto">
      <div class="w-full flex flex-nowrap">
        <div class="content-end w-auto">
            <Logo />
        </div>
        <div class="content-end w-auto lg:flex-grow-0 flex-grow">
          <Inventory />
        </div>
        <div class="content-end w-auto order-6">
          <div class="user">
            <div class="user-company">Volkswagon</div>
            <div class="account">
              <span class="button button--secondary weight-bold m-0">KS<sup class="account-number">2</sup></span>
            </div>
          </div>
        </div>
        <div class="content-end w-auto lg:flex-grow-1 flex-grow">
          <Navigation :navigation="[{link: '#', title: 'Products'}, {link: '#', title: 'Reviews'}]" />
        </div>
      </div>
    </div>
  </div>
  <div class="filters">
    <div class="container m-auto">
      <div class="w-full flex flex-nowrap">
        <div class="content-end w-auto">
          <nav>
            <ul class="menu">
              <li class="selected"><a href="#">All</a></li>
              <li><a href="#">Groups</a></li>
              <li><a href="#">Segments</a></li>
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageHeader',
  props: {
    // msg: String
  }
}
</script>

<style scoped>
.logo {
  padding: 1rem 0 1.3rem 0;
}
.inventory {
  padding: 1rem 1rem 1.3rem 1rem;
}
</style>