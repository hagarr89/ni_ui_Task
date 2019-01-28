<template>
  <div id="app">
    <app-header></app-header>
    <router-view/>
    <app-footer></app-footer>
  </div>
</template>

<script>
import appFooter from '@/components/layout/appFooter'
import appHeader from '@/components/layout/appHeader'

export default {
  name: 'App',
  components:{
    appFooter,
    appHeader
  }
};
</script>

<style>
</style>
