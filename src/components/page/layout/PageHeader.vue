<script setup>
import Logo from '@/components/icons/LogoBeta.vue'
import Inventory from '@/components/Inventory.vue'
import Navigation from '@/components/Navigation.vue'

const TopMenuNav = [
  {url: '#', title: 'Products', className: 'selected' },
  {url: '#', title: 'Reviews'},
  {url: '#', title: 'Requests'},
  {url: '#', title: 'Appointments'}
];
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
          <Navigation
              class-name="top-nav"
              :navigation="TopMenuNav"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style>
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

.account
{
  position: relative;
}

.account .button
{
  color: #171e31;
  background-color: #D5D5D5;
  border-color: #D5D5D5;
}

.account .account-number
{
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
}
</style>