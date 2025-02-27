<script setup>
import PageHeader from '@/components/page/layout/PageHeader.vue'
import PageSubMenu from '@/components/page/layout/PageSubMenu.vue'
import PageFooter from '@/components/page/layout/PageFooter.vue'
import ProductList from '@/components/ProductList.vue'
</script>

<template>
  <header>
    <PageHeader />
  </header>
  <aside>
    <PageSubMenu />
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
