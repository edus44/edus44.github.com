<template>
  <div id="app">
    <h1>Eduardo Hidalgo</h1>
    <h2>web software engineer</h2>
    <div class="links">
      <a href="https://www.linkedin.com/in/eduardohidalgoh">
        <i class="fab fa-linkedin-in"></i>
      </a>
      <a href="https://github.com/edus44">
        <i class="fab fa-github"></i>
        edus44
      </a>
    </div> 
    
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
* {
  -webkit-tap-highlight-color: rgba(0,0,0,0);
  -webkit-tap-highlight-color: transparent;
  -webkit-user-select: none;
  user-select: none;
}

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
  font-size: 2.2rem;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-top: 5rem;
  margin-bottom: 0;
}
h2 {
  margin: 0;
  font-weight: normal;
}
.links {
  margin-top: 2rem;
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
