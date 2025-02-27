<script setup>
import Header from "@/components/elements/Header.vue";
import Button from "@/components/elements/Button.vue";
import PageFilter from '@/components/page/layout/PageFilter.vue'

import { onMounted } from 'vue'
onMounted(() => {
  window.addEventListener('load', () => {
    products.loadProducts();
  })
})

const products = {
  tableId: 'page-content-data__table',
  perPage: 15,
  currentPage: 1,
  totalProducts: 0,
  totalPages: 1,
  allProducts: null,
  firstButton: null,
  previousButton: null,
  nextButton: null,
  lastButton: null,
  pageNumberElement: null,
  totalPagesElement: null,
  pageDetailsElement: null,
  filterButtons: null,
  sort: null,
  sorted: [],

  /**
   * Fetch and append products to the table
   */
  loadProducts(productFilters)
  {
    this.setupPageButtons();
    this.fetchProducts((error, products) => {
      if (error) {
        alert(error)
      }
      else {
        if (typeof productFilters !== 'undefined') {
          let numberOfProductFilters = Object.keys(productFilters).length;
          this.allProducts = products
              .filter(function (v) {
                let found = 0;
                Object.entries(productFilters).forEach(([filterType, filterValues]) => {
                  if (
                      typeof v[filterType] !== 'undefined'
                      && filterValues.includes(v[filterType])
                  ) {
                    found++;
                  }
                });

                return found === numberOfProductFilters;
              });
        } else {
          productFilters = Array();
          this.allProducts = products;
        }

        this.totalProducts = this.allProducts.length;
        this.totalPages = Math.ceil(this.totalProducts / this.perPage);
        this.getFilters(products, productFilters);
        this.getPage(this.currentPage);
      }
    });
  },

  /**
   * Setup pagination events
   */
  setupPageButtons()
  {
    this.firstButton = document.getElementById("first-button");
    this.firstButton.addEventListener('click', firstPage);

    this.previousButton = document.getElementById("previous-button");
    this.previousButton.addEventListener('click', previousPage);

    this.nextButton = document.getElementById("next-button");
    this.nextButton.addEventListener('click', nextPage);

    this.lastButton = document.getElementById("last-button");
    this.lastButton.addEventListener('click', lastPage);

    this.sort = document.getElementsByClassName("sort");
    for (let i = 0; i < this.sort.length; i++) {
      this.sort[i].addEventListener('click', sortProducts, false);
    }

    let filterButton = document.getElementById("apply-filter");
    filterButton.addEventListener('click', applyFilter);

    this.pageNumberElement = document.getElementById("page-number");
    this.totalPagesElement = document.getElementById("total-pages");
    this.pageDetailsElement = document.getElementById("page-details");

    this.filterButtons = document.getElementsByClassName("filter-button");
    for (let i = 0; i < this.filterButtons.length; i++) {
      this.filterButtons[i].addEventListener('click', toggleFilterPanel);
    }
  },

  /**
   * this.sort products
   *
   * @param e
   */
  sortProducts(e)
  {
    const sort_by = (field, reverse) => {
      const key = function (x) {
        if (field.indexOf('.') !== -1) {
          let fields = field.split('.');
          for (let i = 0; i < fields.length; i++) {
            x = x[fields[i]];
          }
          return x;
        }
        return x[field]
      };

      reverse = !reverse ? 1 : -1;

      return function(a, b) {
        return a = key(a), b = key(b), reverse * ((a > b) - (b > a));
      }
    }

    let sortIcon = e.target;
    let field = sortIcon.dataset.field;
    let currentSortOrder = (typeof this.sorted[field] !== 'undefined')
        ? this.sorted[field] : '';
    let sortOrder = '';

    if (currentSortOrder === '') {
      sortOrder = 'asc';
    } else if (currentSortOrder === 'asc') {
      sortOrder = 'desc';
    }

    this.sorted[field] = sortOrder;
    this.allProducts.sort(sort_by(field, (sortOrder === 'desc')));

    for (let i = 0; i < this.sort.length; i++) {
      this.removeClass(this.sort[i], 'fa-sort-asc');
      this.removeClass(this.sort[i], 'fa-sort-desc');
    }

    this.removeClass(e.target, 'fa-sort-' + currentSortOrder);
    this.addClass(e.target, 'fa-sort-' + sortOrder);

    this.getPage(1);
  },

  /**
   * Fetch the product from Fake Store API
   *
   * @param callback
   */
  fetchProducts(callback)
  {
    fetch('https://fakestoreapi.com/products')
        .then(response => response.json())
        .then(json => callback(null, json))
        .catch(error => callback(error, null))
  },

  /**
   * Append a page of products to the data table
   *
   * @param page
   */
  getPage(page)
  {
    let start = (page-1) * this.perPage;
    let productCount = this.allProducts.length;

    this.currentPage = page;

    if (start > productCount) {
      start = this.allProducts.length / this.perPage;
    } else if (start < 0) {
      start = 0
    }
    let end = start + this.perPage;
    if (end > productCount) {
      end = productCount
    }

    let content = document.createElement("tbody");
    for (let i = start; i < end; i++) {
      let product = this.allProducts[i];
      this.appendProduct(product, content);
    }

    let table = document.getElementById(this.tableId).getElementsByTagName('tbody')[0];
    table.replaceWith(content);

    this.updatePage(start, end);
  },

  /**
   * Append a product to the table
   *
   * @param product
   * @param table
   */
  appendProduct(product, table)
  {
    let tr = document.createElement('tr');
    tr.innerHTML = '<td><img class="imgbox" src="' + product.image + '" /></td>' +
        '<td><a href="#' + product.id +'">' + product.title + '</a></td>' +
        '<td>' + product.id + '</td>' +
        '<td>' + product.category + '</td>' +
        '<td>' + product.rating.rate + '(' + product.rating.count + ')</td>' +
        '<td>' + product.price + '</td>';

    table.appendChild(tr);
  },

  /**
   * Update page details and buttons
   *
   * @param start
   * @param end
   */
  updatePage(start, end)
  {
    if (this.currentPage === 1) {
      this.addClass(this.firstButton, "disabled");
      this.addClass(this.previousButton, "disabled");
    } else {
      this.removeClass(this.firstButton, "disabled");
      this.removeClass(this.previousButton, "disabled");
    }

    if (this.currentPage === this.totalPages) {
      this.addClass(this.nextButton, "disabled");
      this.addClass(this.lastButton, "disabled");
    } else {
      this.removeClass(this.nextButton, "disabled");
      this.removeClass(this.lastButton, "disabled");
    }

    this.pageNumberElement.innerHTML = this.currentPage;
    this.totalPagesElement.innerHTML = this.totalPages;
    this.pageDetailsElement.innerHTML = (start+1) + '-' + end + ' of ' + this.totalProducts;
  },

  /**
   * Go to first page
   */
  firstPage()
  {
    if (this.currentPage <= 1) {
      return;
    }
    this.getPage(1)
  },

  /**
   * Go to previous page
   */
  previousPage()
  {
    if (this.currentPage <= 1) {
      return;
    }
    this.getPage(this.currentPage-1)
  },

  /**
   * Go to next page
   */
  nextPage()
  {
    if (this.currentPage >= this.totalPages) {
      return;
    }
    this.getPage(this.currentPage+1)
  },

  /**
   * Go to last page
   */
  lastPage()
  {
    if (this.currentPage >= this.totalPages) {
      return;
    }
    this.getPage(this.totalPages)
  },

  /**
   * Open/Close filter
   *
   * @param open true|false // toggle if left empty
   */
  toggleFilterPanel(open)
  {
    const filterPanel = document.getElementById("filter-panel");
    const overlayPanel = document.getElementById("overlay");
    const forceOpen = (typeof open !== 'undefined') ? open : true;

    if (forceOpen && (" " + filterPanel.className + " ").indexOf(" open ") === -1) {
      console.log('OFF');
      this.addClass(filterPanel, "open");
      this.addClass(overlayPanel, "open");
    } else {
      console.log('ON');
      this.removeClass(filterPanel, "open");
      this.removeClass(overlayPanel, "open");
    }
  },

  /**
   * Apply filter
   */
  applyFilter()
  {
    let filter = {
      'category': []
    };

    let categoryInputElements = document.getElementsByName('category[]');

    if (categoryInputElements.length > 0) {
      Object.entries(categoryInputElements).forEach(([filterType, filterValue]) => {
        if (filterValue.checked) {
          filter['category'].push(filterValue.value);
        }
      });
    }

    this.loadProducts(filter);
    this.toggleFilterPanel(false);
  },

  /**
   * Get product filters
   *
   * @param products
   * @param productFilters
   */
  getFilters(products, productFilters)
  {
    let replaceHTML = '';
    let filterGroups = document.getElementById("filter_groups");

    replaceHTML += this.getCategories(products, productFilters);

    filterGroups.innerHTML = replaceHTML;
  },

  /**
   * List available categories in the filter
   *
   * @param products
   * @param productFilters
   *
   * @return string
   */
  getCategories(products, productFilters)
  {
    const categories = products
        .map(item => item.category)
        .filter(function (v, i, self) {
          return i === self.indexOf(v);
        });

    let list = '';
    Object.entries(categories).forEach(([filterType, categoryName]) => {
      list += this.appendCategory(categoryName, productFilters);
    });

    return '' +
        '<div class="filter__group">\n' +
        '    <div class="filter__title">Category</div>\n' +
        '    <div class="filter__list">\n' +
        '        ' + list +
        '    </div>\n' +
        '</div>\n';
  },

  /**
   * Append a product to the table
   *
   * @param categoryName
   * @param productFilters
   *
   * @return string
   */
  appendCategory(categoryName, productFilters)
  {
    const checked = productFilters.hasOwnProperty('category') && productFilters.category.includes(categoryName)
        ? 'checked="checked"'
        : '';

    return '' +
        '<label>' +
        '    <input type="checkbox" name="category[]" ' + checked + ' value="' + categoryName + '"> ' + categoryName +
        '</label>';
  },

  /**
   * Remove class from element
   *
   * @param element
   * @param className
   */
  removeClass(element, className)
  {
    element.classList.remove(className);
  },

  /**
   * Add class from element
   *
   * @param element
   * @param className
   */
  addClass(element, className)
  {
    element.classList.add(className);
  }
}

function firstPage()
{
  products.firstPage();
}

function previousPage()
{
  products.previousPage();
}

function nextPage()
{
  products.nextPage();
}

function lastPage()
{
  products.lastPage();
}

function sortProducts(e)
{
  products.sortProducts(e);
}

function applyFilter()
{
  products.applyFilter();
}

function toggleFilterPanel()
{
  products.toggleFilterPanel();
}

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
                class-name="button--secondary filter-button"
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

  <PageFilter />

  <div
      id="overlay"
      class="filter-button"
  ></div>
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


  /* Main
  –––––––––––––––––––––––––––––––––––––––––––––––––– */
  main
  {
    background-color: #F2F2F2;
    padding: 2rem 0;
  }

  .page-content
  {
    background-color: white;
    box-shadow: 0 1px 2px #cccccc;
    border-radius: 1rem;
    padding: 0;
  }

  .page-content-data
  {
    overflow: auto;
  }

  .page-content-header
  {
    padding: 2rem 2rem 0 2rem;
  }

  .page-content-footer
  {
    padding: 0 2rem 2rem 2rem;
  }

  .imgbox
  {
    width: 40px;
    height: 40px;
    background-color: white;
    border: 1px solid #646464;
    display: inline-block;
  }

  .pagination--no-text .button span
  {
    display: none;
  }

  /* Panel
  –––––––––––––––––––––––––––––––––––––––––––––––––– */
  .panel
  {
    z-index: 1000;
    position: fixed;
    overflow: hidden;
    top: 0;
    bottom: 0;
    right: -300px;
    width: 300px;
    transition: right 0.5s;
    background-color: white;
  }

  .open.panel
  {
    right: 0;
  }

  .panel__header
  {
    background-color: #FFF;
    box-shadow: 0 5px 10px #646464;
    position: relative;
    padding: 1rem 2rem;
  }

  .panel__title
  {
    text-align: center;
  }

  .panel__close-button
  {
    position: absolute;
    top: 1rem;
    right: 1rem;
  }

  .panel__close-button span
  {
    display: none;
  }

  .panel__content-wrapper
  {
    max-height: 100%;
    overflow: auto;
  }

  .panel__content
  {
    padding: 2rem 2rem 6rem 2rem;
  }

  .filter__title
  {
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  .filter__list label
  {
    font-weight: normal;
    display: block;
    margin-bottom: .5rem;
  }

  .filter__list input
  {
    margin: 0;
  }

  .panel__footer
  {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    box-shadow: 0 -5px 10px #646464;
    padding: 1rem 2rem;
    background-color: #FFF;
  }

  #apply-filter
  {
    width: 100%;
    margin: 0;
  }

  /* Overlay
  –––––––––––––––––––––––––––––––––––––––––––––––––– */
  #overlay
  {
    position: fixed;
    z-index: 100;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: black;
    opacity: 0.5;
    display: none;
  }

  .open#overlay
  {
    display: block;
  }

</style>