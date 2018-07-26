<template>
  <div class="item">
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
  props: ['name', 'src', 'link'],
}
</script>

<style>
.item {
  background-color: #ccc;
  width: 300px;
  margin: 10px auto;
  padding: 10px 0;
  transform-style: preserve-3d;
  transform: rotateX(-10deg) rotateY(-10deg) rotate(-2deg);
  transition: 0.2s;
  cursor: pointer;
}
.item:hover {
  transform: scale(1.1) rotateX(-10deg) rotateY(-10deg) rotate(-2deg);
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
</style>
