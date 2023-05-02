<template>
  <div id="app">
    <Header />
    <Notes />
  </div>
</template>

<script>
import Header from './components/Header'
import Notes from './components/Notes'

export default {
  name: 'App',
  components: { Header, Notes }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
