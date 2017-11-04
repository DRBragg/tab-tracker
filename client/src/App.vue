<template>
  <div id="app">
    <v-app>
      <page-header />
      <main>
        <v-container>
          <router-view/>
        </v-container>
      </main>
    </v-app>
  </div>
</template>

<script>
import PageHeader from './components/PageHeader'
import HelloWorld from './components/HelloWorld'

export default {
  name: 'app',
  components: {
    PageHeader,
    HelloWorld
  }
}
</script>

<style>

</style>
