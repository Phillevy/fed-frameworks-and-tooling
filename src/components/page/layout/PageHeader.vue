<script setup>
import { ref } from 'vue'

import Logo from '@/components/icons/LogoBeta.vue'
import Inventory from '@/components/Inventory.vue'
import Navigation from '@/components/Navigation.vue'
import ButtonCounter from '@/components/elements/ButtonCounter.vue'

const TopMenuNav = ref([
  {url: '#', title: 'Products', className: 'selected' },
  {url: '#', title: 'Reviews'},
  {url: '#', title: 'Requests'},
  {url: '#', title: 'Appointments'}
]);
</script>

<template>
  <div class="header">
    <div class="container m-auto">
      <div class="w-full flex flex-wrap">
        <div class="content-end w-auto">
          <Logo class="logo" />
        </div>
        <div class="content-end w-auto grow md:grow-0">
          <Inventory class="inventory" />
        </div>
        <div class="content-end w-auto md:order-last">
          <div class="user">
            <div class="user-company">Volkswagon</div>
            <div class="account">
              <ButtonCounter
                  title="KS"
                  subtitle="2"
                  id="apply-filter"
                  class-name="button button--tertiary weight-bold m-0"
              />
            </div>
          </div>
        </div>
        <div class="content-end w-full md:w-auto grow">
          <Navigation
              class-name="top-nav"
              :navigation="TopMenuNav"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.logo
{
  padding: 1rem 0 1.3rem 0;
}

.inventory
{
  display: flex;
  align-items: flex-end;
  font-size: 1.25rem;
  font-weight: bold;
  padding: 1rem 1rem 1.3rem 1rem;
}

.user
{
  display: flex;
  align-items: flex-end;
  padding: 1rem 0 1.3rem 0;
  height: 2.7rem;
}

.user-company
{
  padding-right: 1rem;
}
</style>
