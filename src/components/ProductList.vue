<template>
  <main class="list">
    <div class="container">
      <div class="page-navigation">
        <div class="row">
          <div class="col-auto flex-grow-1">
            <h1>Products</h1>
          </div>
          <div class="col-auto">
            <button class="button no-border"><i class="fa-solid fa-file-import"></i> Import</button>
            <button class="button no-border"><i class="fa-solid fa-file-export"></i> Export</button>
            <button class="button button--primary"><i class="fa-solid fa-plus"></i> Add Product</button>
          </div>
        </div>
      </div>

      <div class="page-content">
        <div class="page-content-header">
          <div class="row">
            <div class="col-auto flex-grow-1">
              <button class="button button--secondary filter-button"><i class="fa-solid fa-filter"></i> Filters</button>
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
                <button class="button button--secondary" id="first-button">
                  <i class="fa-solid fa-angle-double-left"></i><span> First Page</span>
                </button>
                <button class="button button--secondary" id="previous-button">
                  <i class="fa-solid fa-angle-left"></i><span> Previous Page</span>
                </button>
                <div class="page d-inline-block">Page
                  <span class="button button--secondary" id="page-number">1</span> of
                  <span id="total-pages"></span>
                </div>
                <button class="button button--secondary" id="next-button">
                  <i class="fa-solid fa-angle-right"></i><span> Next Page</span>
                </button>
                <button class="button button--secondary" id="last-button">
                  <i class="fa-solid fa-angle-double-right"></i><span> Last Page</span>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>

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
        <button class="button button--secondary" id="apply-filter">Apply Filter</button>
      </div>
    </div>
  </aside>

  <div id="overlay" class="filter-button"></div>
</template>

<script>
export default {
  name: 'ProductList',
  props: {
    msg: String
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
