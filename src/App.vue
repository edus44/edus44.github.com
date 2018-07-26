<template>
  <div id="app">
    <h1>Eduardo Hidalgo</h1>
    <div class="links">
      <a href="https://github.com/edus44">
        <i class="fab fa-linkedin-in"></i>
      </a>
      <a href="https://github.com/edus44">
        <i class="fab fa-github"></i>
        edus44
      </a>
    </div>
    
    <div class="groups">
      <a 
        v-for="group in groups" :key="group.id" 
        :href="`#${selected == group.id ? '' : group.id}`" 
        :class="{active: selected == group.id}"
      >
        {{ group.name }}
        <div class="icon">
        <i class="fas fa-chevron-down" ></i>
        </div>
      </a>
    </div>

    <transition-group
      name="fade"
      :appear="true"
      @before-enter="beforeEnter"
      @after-enter="afterEnter"
      @before-leave="beforeLeave"
      @after-leave="afterEnter"
      tag="div"
      class="items"

    >
      <Item 
        v-for="(item,index) in selectedItems" 
        v-bind="item" 
        :key="item.name"
        :data-index="index"
        :data-len="selectedItems.length"
      />
    </transition-group>

  </div>
</template>

<script>
import projects from './projects'
import games from './games'
import Item from './Item'

export default {
  components: {
    Item,
  },
  data: () => ({
    selected: '',
    groups: [
      {
        id: 'projects',
        name: 'projects',
        items: projects,
      },
      {
        id: 'games',
        name: 'games',
        items: games,
      },
    ],
  }),
  computed: {
    selectedItems() {
      const group = this.groups.find(x => x.id == this.selected)
      return group ? group.items : []
    },
  },
  mounted() {
    window.addEventListener('hashchange', this.syncHash, false)
    setTimeout(this.syncHash, 100)
  },
  methods: {
    syncHash() {
      const id = location.hash.replace('#', '')

      const exists = this.groups.some(group => group.id == id)
      this.selected = exists ? id : ''
    },
    beforeEnter(el) {
      el.style.transitionDelay = el.dataset.index * 50 + 'ms'
    },
    afterEnter(el) {
      el.style.transitionDelay = '0ms'
    },
    beforeLeave(el) {
      el.style.transitionDelay = (el.dataset.len - el.dataset.index) * 50 + 'ms'
    },
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

.groups {
  margin: 4rem 0;
}

.groups a {
  color: rgb(20, 16, 14);
  text-decoration: none;
  display: inline-block;
  margin: 0 1rem;
  font-size: 1.4rem;
  font-weight: bold;
  transition: 0.4s;
}

.groups a:hover {
  color: rgb(28, 160, 149);
}
.groups a.active {
  color: rgb(28, 160, 149);
}

.groups a .icon {
  transition: 0.4s transform;
  margin-top: 0.5rem;
}
.groups a.active .icon {
  transform: translateY(10px);
}

.groups a i {
  font-size: 2rem;
  transition: 0.6s transform;
}
.groups a.active i {
  transform: rotate(-180deg);
}

.items {
  perspective: 800px;
}
</style>
