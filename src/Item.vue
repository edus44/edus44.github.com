<template>
  <div class="item" :class="{active}" @click="$emit('toggle')">
    <!-- <a :href="link"> -->
    <b>{{name}}</b>

    <p >
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Vel, at cumque, neque earum unde quas eligendi vero magni aperiam similique optio, quia magnam totam hic doloremque tempora modi ut fuga!
    </p>
    
    <!-- <a :href="src">
      <i class="fas fa-code"></i>
    </a> -->
  </div>
</template>

<script>
export default {
  props: ['name', 'src', 'link', 'active'],
}
</script>

<style>
.item {
  /* background-color: #eee; */
  border-bottom: 1px solid #eee;
  width: 300px;
  margin: 15px auto;
  padding: 10px 0;
  transition: 0.5s;
  cursor: pointer;
  height: 2rem;
  overflow: hidden;
  text-align: left
}
.item.active {
  border-bottom-color: rgb(28, 160, 149);
  height: 8rem;
}

.item b{
  font-size: 1.4rem;
}
.item.active b{
  color: rgb(28, 160, 149);
}

.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.6s;
}
.fade-enter {
  opacity: 0;
  transform: translateY(10px);
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
