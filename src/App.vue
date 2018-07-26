<template>
  <div id="app">
    <!-- <h1>Eduardo Hidalgo</h1>
    <div class="links">
      <a href="https://github.com/edus44">
        <i class="fab fa-linkedin-in"></i>
      </a>
      <a href="https://github.com/edus44">
        <i class="fab fa-github"></i>
        edus44
      </a>
    </div> -->
    
    <Groups/>

  </div>
</template>

<script>
import Groups from './Groups'

export default {
  components: {
    Groups,
  },
}
</script>

<style>
body,
html {
  margin: 0;
  padding: 0;
  font-size: 10px;
  text-align: center;
  cursor: default;
}
body {
  font-family: 'Nunito', sans-serif;
  color: rgb(20, 16, 14);
}
h1 {
  font-size: 2rem;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-top: 3rem;
}
.links a {
  color: rgb(20, 16, 14);
  text-decoration: none;
  display: inline-block;
  margin: 0 1rem;
  font-size: 1.4rem;
  font-weight: bold;
  transition: 0.2s;
}
.links a:hover {
  color: rgb(28, 160, 149);
}
</style>
