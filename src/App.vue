<script>
import Home from './components/Home.vue'
import NotFound from './components/NotFound.vue'

const routes = {
  '': Home,
  '/': Home,
  '#/es': Home 
}

export default {
  data() {
    return {
      currentPath: window.location.hash
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath]
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
		  this.currentPath = window.location.hash
		})
  }
}
</script>

<template>
  <a href="/#/es">Spanish</a>
  <component :is="currentView" />
</template>