<template>
  <v-app>
    <div class="background">
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
import Chat from './components/QuizPage';

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