<script setup>
import PageHeader from './components/PageHeader.vue'
import TheWelcome from './components/TheWelcome.vue'
</script>

<template>
  <header>
    <PageHeader />
  </header>

  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld class="text-3xl underline" msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>

</style>
