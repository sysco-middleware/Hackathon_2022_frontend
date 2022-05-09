<template>
  <v-app>
    <div class="background">
    <v-app-bar
      app
      color="#3F1651"
      dark
    >

    </v-app-bar>
      <br>
    <v-main>
      <MainPage/>
      <Chat/>
    </v-main>
    </div>
  </v-app>
</template>

<script>
import MainPage from './components/MainPage';
import Chat from './components/Chat';

export default {
  name: 'App',

  components: {
    MainPage,
    Chat,
  },

};
</script>

<style>
.background{
  background-color: black;
}
</style>