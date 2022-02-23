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
  },
  methods: {
    reloadPage(ev) {
      window.location.href = ev.currentTarget
      window.location.reload();
    },
    isEs() {
      return window.location.hash =='#/es' ? true : false
    }
  }
}
</script>

<template>
  <a v-if="isEs()" href="/" @click="reloadPage($event)">English</a>
  <a  v-else href="/#/es" @click="reloadPage($event)">Español</a> 
  <component :is="currentView" />
</template>