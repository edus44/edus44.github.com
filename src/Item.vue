<template>
  <div class="item" :class="{active}" @click="$emit('toggle')">
    <!-- <a :href="link"> -->
    <a>
      <b>{{name}}</b>
    </a>

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
  background-color: #eee;
  width: 300px;
  margin: 15px auto;
  padding: 10px 0;
  transform-style: preserve-3d;
  transform: rotateX(-10deg) rotateY(-10deg) rotate(-2deg);
  transition: 0.5s;
  cursor: pointer;
  height: 1.5rem;
  overflow: hidden;
}
.item:hover {
}
.item.active {
  height: 8rem;
  transform: rotateX(-10deg) rotateY(-10deg) rotate(-2deg) translateX(10px) translateZ(30px);
}
.item a {
  text-decoration: none;
  color: black;
}

.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.6s;
  transform: translateY(0) rotateX(-10deg) rotateY(-10deg) rotate(-2deg);
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-30px) rotateX(90deg) rotateY(10deg) rotate(2deg);
}

.fade-move {
  /* display: none; */
}
</style>
