<template>
  <v-container>
    <v-row justify="space-around">
      <v-card width="100%" color="#E6E1EF">
        <v-img
            height="100px"
            src="https://images.unsplash.com/photo-1419242902214-272b3f66ee7a?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2113&q=80"
        >
          <v-app-bar
              flat
              color="rgba(0, 0, 0, 0)"
          >
              <div class="mainTitle">Cegal Twitch Stream</div>
            <v-spacer></v-spacer>
          </v-app-bar>
        </v-img>

        <v-card-text>
          <v-row class="side1">
            <v-col class="col-8">
          <iframe
              src="https://player.twitch.tv/moonunit666&parent=https://twitchhackathonfrontend.azurewebsites.net/"
              height="660"
              width="775"
              allowfullscreen>
          </iframe>
            </v-col>
            <v-col class="col-4">
              <h2 class="otherFont">This stream powered by:</h2>

              <img src="../cegalLogo.png" alt="Logo" width="100%" height="15%">
              <br>
              <h2 class="otherFont">...And this yeti! </h2>

              <img src="../yeti.jpg" alt="Logo" width="100%" height="45%">
              <br>
              <h2 class="otherFont">Please answer by clicking the following buttons:</h2>
              <v-btn class="button" depressed color="#E0C2F2"  @click="clickButton($event)">
                A
              </v-btn>
              <v-btn
                  depressed
                  color="#3F1651"
                  class="white--text button"
                  @click="clickButton($event)"
              >
               B
              </v-btn>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-row>
  </v-container>
</template>

<script>

export default {
  name: "Chat",
  data() {
    return{
      question:
        {
          scene: "StartStream",
          answer:"",
        }
    }
  },
  methods: {
    fetchSomething: function(){
      //example of a get
      fetch('https://ghibliapi.herokuapp.com/films')
          .then(response => response.json())
          // eslint-disable-next-line no-console
          .then(data => console.log(data));
    },

    clickButton: function(item) {
      this.question.answer = item.target.outerText
      this.postRequest()
    },

    postRequest: function() {
      const data = this.question;

      fetch('https://twitchcommandreceiver.azurewebsites.net/sendAction', {
        method: 'POST', // or 'PUT'
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(data),
      })
          .then(response => response.json())
          .then(data => {
            // eslint-disable-next-line no-console
            console.log('Success:', data);
          })
          .catch((error) => {
            // eslint-disable-next-line no-console
            console.error('Error:', error);
          });
    }

  },
};
</script>


<style scoped>
button{
  width: 50%;
  min-height: 60px;
  max-height: 60px;
}
.mainTitle{
font-size: 50px;
  color: white ;
  font-family: "Papyrus", Times, serif;
  margin-left: 40%;
  margin-top: 5%;
  font-weight: bold;
}
.otherFont{
  font-family: "Papyrus", Times, serif;
  padding:10px;
}
.v-application .text-h6 {
  margin-left: 40%;
}
</style>