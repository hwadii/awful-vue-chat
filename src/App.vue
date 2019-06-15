<template>
  <div id="app">
    <v-app id="inspire">
      <Chat />
    </v-app>
  </div>
</template>

<script>
import Chat from "./components/Chat";

export default {
  name: "app",
  components: {
    Chat
  }
};
</script>

<style>
#app {
  font-family: "Open Sans", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#inspire {
  background: #ECE5DD;
}
</style>
