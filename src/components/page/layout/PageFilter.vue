<script setup>
import Button from "@/components/elements/Button.vue";
</script>

<template>
  <aside class="panel" id="filter-panel">
    <div class="panel__header">
      <div class="panel__title">Filters</div>
      <div class="panel__close-button filter-button">
        <i class="fa-solid fa-close"></i><span> Close Filter</span>
      </div>
    </div>
    <div class="panel__content-wrapper">
      <div class="panel__content" id="filter_groups">
      </div>
      <div class="panel__footer">
        <Button
            title="Apply Filter"
            id="apply-filter"
            class-name="button--secondary"
        />
      </div>
    </div>
  </aside>
</template>

