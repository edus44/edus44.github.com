<template>
  <div>
    
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
        :active="index==activeItem"
        @toggle="toggle(index)"
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
    activeItem: -1,
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
    toggle(index) {
      this.activeItem = this.activeItem === index ? -1 : index
    },
    syncHash() {
      const id = location.hash.replace('#', '')

      const exists = this.groups.some(group => group.id == id)
      this.selected = exists ? id : ''
      this.activeItem = -1
    },
    beforeEnter(el) {
      el.style.transitionDelay = el.dataset.index * 50 + 'ms'
    },
    afterEnter(el) {
      el.style.transitionDelay = '0ms'
    },
    beforeLeave(el) {
      el.style.transitionDelay = (el.dataset.len - el.dataset.index) * 25 + 'ms'
    },
  },
}
</script>

<style>
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
  /* transform: rotateX(-10deg) rotateY(-10deg) rotate(-2deg); */
}
</style>
