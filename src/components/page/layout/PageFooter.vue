<script setup>
import Logo from '@/components/icons/Logo.vue'
import Navigation from '@/components/Navigation.vue'

const FooterMenuNav = [
  {url: '#', title: 'Terms & conditions'},
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
    <div class="w-full flex flex-nowrap justify-between">
      <div class="content-end w-auto">
        <Logo />
      </div>
      <div class="w-auto lg:flex-grow-0 flex-grow content-center">
        <Navigation
            class-name="bottom-nav"
            :navigation="FooterMenuNav"
        />
      </div>
      <div class="w-auto content-center">
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