<script setup>
import PageHeader from './components/PageHeader.vue'
import PageFilter from './components/PageFilter.vue'
import ProductList from './components/ProductList.vue'
import PageFooter from './components/PageFooter.vue'
</script>

<template>
  <header>
    <PageHeader />
  </header>
  <aside>
    <PageFilter />
  </aside>
  <main>
    <div class="container">
      <ProductList />
    </div>
  </main>
  <footer>
    <PageFooter />
  </footer>
</template>

<style scoped>

</style>
