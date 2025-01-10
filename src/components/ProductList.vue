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
        <div class="page-content-header flex">
          <div class="w-auto grow">
            <Button
                title="Filters"
                icon="filter"
                class-name="button--secondary"
            />
          </div>
          <div class="w-auto">
            <p id="page-details">1-15 of 20</p>
          </div>
        </div>

        <div class="page-content-data">
          <table
              class="alternate-rows"
              id="page-content-data__table"
          >
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
            <tr>
              <td><div class="imgbox"></div></td>
              <td><a href="#">Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops</a></td>
              <td>1</td>
              <td>Men’s clothing</td>
              <td>3.9 (120)</td>
              <td>£109.95</td>
            </tr>
            <tr>
              <td><div class="imgbox"></div></td>
              <td><a href="#">Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops</a></td>
              <td>1</td>
              <td>Men’s clothing</td>
              <td>3.9 (120)</td>
              <td>£109.95</td>
            </tr>
            <tr>
              <td><div class="imgbox"></div></td>
              <td><a href="#">Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops</a></td>
              <td>1</td>
              <td>Men’s clothing</td>
              <td>3.9 (120)</td>
              <td>£109.95</td>
            </tr>
            </tbody>
          </table>
        </div>

        <div class="page-content-footer flex justify-end">
          <div class="pagination pagination--no-text flex items-center p-4">
            <Button
                title="First Page"
                id="first-button"
                icon="angle-double-left"
                class-name="button--secondary m-2"
            />
            <Button
                title="Previous Page"
                id="previous-button"
                icon="angle-left"
                class-name="button--secondary m-2"
            />
            <div class="page flex items-center">
              Page
              <Button
                  title="1"
                  id="page-number"
                  class-name="button--secondary m-2"
              /> of
              <span id="total-pages"></span>
            </div>
            <Button
                title="Next Page"
                id="next-button"
                icon="angle-right"
                class-name="button--secondary m-2"
            />
            <Button
                title="Last Page"
                id="last-button"
                icon="angle-double-right"
                class-name="button--secondary m-2"
            />
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

<style>
  .page-navigation {
    @apply pb-8;
  }
  .page-content
  {
    @apply bg-white shadow-sm rounded-2xl;
  }
  .page-content-header
  {
    @apply p-8;
  }
  .pagination button span
  {
    display: none;
  }
  .pagination .page button span
  {
    display: inline-block;
  }
</style>