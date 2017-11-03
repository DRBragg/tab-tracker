<template>
    <v-toolbar dark fixed class="cyan">
      <v-toolbar-title class="mr-4">
        <span @click="navigateTo({name: 'root'})">Tab Tacker</span>
      </v-toolbar-title>
      <v-toolbar-items>
        <v-btn flat dark>Browse</v-btn>
      </v-toolbar-items>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn flat dark @click="navigateTo({name: 'login'})">
          Log In
        </v-btn>
        <v-btn flat dark @click="navigateTo({name: 'register'})">
          Sign Up
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  }
}
</script>

<style>


</style>
