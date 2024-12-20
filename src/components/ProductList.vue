<script setup>
import Header from "@/components/elements/Header.vue";
import Button from "@/components/elements/Button.vue";
</script>

<template>
  <div class="container w-auto m-auto">
      <div class="page-navigation">
        <div class="justify-between flex">
          <Header title="Products" />
          <div class="action-buttons">
            <Button
                title="Import"
                icon="file-import"
            />
            <Button
                title="Export"
                icon="file-export"
            />
            <Button
                title="Add Product"
                icon="plus"
                class-name="button--primary"
            />
          </div>
        </div>
      </div>

      <div class="page-content">
        <div class="page-content-header">
          <div class="row">
            <div class="col-auto flex-grow-1">
              <Button
                  title="Filters"
                  icon="filter"
                  class-name="button--secondary"
              />
            </div>
            <div class="col-auto">
              <p id="page-details"></p>
            </div>
          </div>
        </div>

        <div class="page-content-data">
          <table class="alternate-rows" id="page-content-data__table">
            <thead>
            <tr>
              <th>Image</th>
              <th>Title <i class="fa-solid fa-sort sort" data-field="title"></i></th>
              <th>Product ID <i class="fa-solid fa-sort sort" data-field="id"></i></th>
              <th>Category <i class="fa-solid fa-sort sort" data-field="category"></i></th>
              <th>Rating <i class="fa-solid fa-sort sort" data-field="rating.rate"></i></th>
              <th>Price <i class="fa-solid fa-sort sort" data-field="price"></i></th>
            </tr>
            </thead>
            <tbody>
            </tbody>
          </table>
        </div>

        <div class="page-content-footer">
          <div class="row justify-content-end">
            <div class="col-auto">
              <div class="pagination pagination--no-text">
                <Button
                    title="First Page"
                    id="first-button"
                    icon="angle-double-left"
                    class-name="button--secondary"
                />
                <Button
                    title="Previous Page"
                    id="previous-button"
                    icon="angle-left"
                    class-name="button--secondary"
                />
                <div class="page d-inline-block">Page
                  <span class="button button--secondary" id="page-number">1</span> of
                  <span id="total-pages"></span>
                </div>
                <Button
                    title="Next Page"
                    id="next-button"
                    icon="angle-right"
                    class-name="button--secondary"
                />
                <Button
                    title="Last Page"
                    id="last-button"
                    icon="angle-double-right"
                    class-name="button--secondary"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
  </div>

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

  <div id="overlay" class="filter-button"></div>
</template>
