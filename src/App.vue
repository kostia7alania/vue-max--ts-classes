<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script lang='ts'>
import {Vue, Component} from 'vue-property-decorator'

//const AppFooter: () => import('@/components/AppFooter.vue')

@Component
export default class App extends Vue {
  
}
</script>

<style lang="scss"> 
</style>