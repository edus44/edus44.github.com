<template>
  <div>
    <a :href="link">
      <b>{{name}}</b>
    </a>
    
    <a :href="src">
      <i class="fas fa-code"></i>
    </a>
  </div>
</template>

<script>
export default {
  props:['name','src','link']

}
</script>

<style>

</style>
