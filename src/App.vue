<script setup>
import PageHeader from '@/components/page/layout/PageHeader.vue'
import PageSubMenu from '@/components/page/layout/PageSubMenu.vue'
import PageFooter from '@/components/page/layout/PageFooter.vue'
import ProductList from '@/components/ProductList.vue'
</script>

<template>
  <PageHeader />
  <aside>
    <PageSubMenu />
  </aside>
  <main>
    <ProductList />
  </main>
  <PageFooter />
</template>

<style scoped>

</style>
