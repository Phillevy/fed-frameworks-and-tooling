<script setup>
import PageHeader from '@/components/page/layout/PageHeader.vue'
import PageFilter from '@/components/page/layout/PageFilter.vue'
import PageFooter from '@/components/page/layout/PageFooter.vue'
import ProductList from '@/components/ProductList.vue'
</script>

<template>
  <header>
    <PageHeader />
  </header>
  <aside>
    <PageFilter />
  </aside>
  <main>
    <ProductList />
  </main>
  <footer>
    <PageFooter />
  </footer>
</template>

<style scoped>

</style>
