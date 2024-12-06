<script setup>
import Logo from './Logo.vue'
import Navigation from './Navigation.vue'

const FooterMenuNav = [
  {url: '#', title: 'Terms & conditions', className: 'selected' },
  {url: '#', title: 'Help'},
  {url: '#', title: 'FAQ'},
  {url: '#', title: 'Privacy'},
  {url: '#', title: 'Cookies'},
  {url: '#', title: 'Knowledge'},
  {url: '#', title: 'Feature hub'},
  {url: '#', title: 'Documents'},
  {url: '#', title: 'Templates'}
];
</script>
<template>
  <div class="container m-auto">
    <div class="w-full flex flex-nowrap">
      <div class="content-end w-auto">
        <Logo />
      </div>
      <div class="content-end w-auto lg:flex-grow-1 flex-grow">
        <Navigation
            class-name="bottom-nav"
            :navigation="FooterMenuNav"
        />
      </div>
      <div class="content-end w-auto">
        <div class="copyright">
          &copy; Visualsoft 2021
        </div>
      </div>
    </div>
  </div>
</template>

<style>
footer .menu
{
  font-size: 0.875rem;
}

footer .menu a
{
  color: #646464;
  padding: 0.5rem;
}

.copyright
{
  margin: 1rem 0;
}
</style>