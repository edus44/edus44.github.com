<template>
  <div class="item" :class="{ active }">
    <!-- <a :href="link"> -->
    <b @click="$emit('toggle')">{{ name }}</b>

    <div class="item-links">
      <a :href="link" target="_blank" v-if="link">
        Open
        <i class="fas fa-external-link-alt"></i>
      </a>

      <a :href="src" target="_blank" v-if="src">
        Source
        <i class="fas fa-code"></i>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: ['name', 'src', 'link', 'active'],
}
</script>

<style>
.item {
  border-bottom: 1px solid #eee;
  width: 300px;
  margin: 15px auto;
  transition: 0.5s;
  height: 4rem;
  overflow: hidden;
  text-align: left;
}
.item.active {
  border-bottom-color: rgb(28, 160, 149);
  height: 8rem;
}

.item b {
  font-size: 1.4rem;
  height: 4rem;
  display: block;
  line-height: 4rem;
  transition: 0.5s;
  cursor: pointer;
  margin-bottom: 1rem;
}
.item.active b {
  color: rgb(28, 160, 149);
}

.item-links {
  display: flex;
}
.item-links a {
  font-size: 1.2rem;
  display: block;
  flex: 1;
  text-align: center;
  color: rgb(20, 16, 14);
}
.item-links a:hover {
  color: rgb(28, 160, 149);
}
.item-links a i {
  width: 2em;
}

/* fade animation */
.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.6s;
}
.fade-enter {
  opacity: 0;
  transform: translateY(10px);
}
.fade-enter-from,.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
