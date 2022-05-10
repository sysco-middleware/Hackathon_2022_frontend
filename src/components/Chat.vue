<template>
  <v-container>
    <v-row justify="space-around">
      <v-card width="100%">
        <v-img
            height="100px"
            src="https://images.unsplash.com/photo-1419242902214-272b3f66ee7a?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2113&q=80"
        >
          <v-app-bar
              flat
              color="rgba(0, 0, 0, 0)"
          >
            <v-app-bar-nav-icon color="white"></v-app-bar-nav-icon>

            <v-toolbar-title class="text-h6 white--text pl-0">
             Cegal Twitch Stream
            </v-toolbar-title>

            <v-spacer></v-spacer>

            <v-btn
                color="white"
                icon
            >
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </v-app-bar>
        </v-img>

        <v-card-text>
          <v-row>
            <v-col class="col-6">
          <iframe
              src="https://player.twitch.tv/loltyler1"
              height="600"
              width="800"
              allowfullscreen>
          </iframe>
            </v-col>
          </v-row>
        </v-card-text>
        <v-row>
          <v-col class="col-2">
        <v-btn
            class="mx-2"
            dark
            large
            color="purple"
            @click="addItem"
        >
          Send
        </v-btn>
          </v-col>
        </v-row>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>

export default {
  name: "Chat",
  data() {
    return{
      singleMessage: {
        id:"",
        text:"",
      },
      messages: [
        {
          id:'',
          title: '',
          description: ''
        }
      ]
    }
  },
  methods: {
    addItem: function() {
      this.messages.push({
        title: '',
        description: '',
      });
      // eslint-disable-next-line no-console
      console.log(this.messages)
    },
    removeItem: function(index) {
      this.messages.splice(index, 1);
    },
    submitForm() {
      // eslint-disable-next-line no-console
      console.log("test", this.messages)
      this.messages.push(this.singleMessage);
      // eslint-disable-next-line no-console
      console.log("test", this.messages)

    },
  },
};
</script>


<style scoped>

</style>