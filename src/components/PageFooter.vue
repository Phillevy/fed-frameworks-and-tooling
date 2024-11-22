<template>
  <footer class="footer">
    <div class="container">
      <div class="row justify-content-between">
        <div class="col-sm-auto align-content-center">
          <div class="logo">
            <img src="./assets/logo.svg" height="40" width="32" alt="Visualsoft Logo">
          </div>
        </div>
        <div class="col-sm-auto align-content-center">
          <nav>
            <ul class="menu">
              <li><a href="#">Terms &amp; conditions</a></li>
              <li><a href="#">Help</a></li>
              <li><a href="#">FAQ</a></li>
              <li><a href="#">Privacy</a></li>
              <li><a href="#">Cookies</a></li>
              <li><a href="#">Knowledge</a></li>
              <li><a href="#">Feature hub</a></li>
              <li><a href="#">Documents</a></li>
              <li><a href="#">Templates</a></li>
            </ul>
          </nav>
        </div>
        <div class="col-sm-auto align-content-center">
          <div class="copyright">
            &copy; Visualsoft 2021
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'PageFooter',
  props: {
    // msg: String
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
