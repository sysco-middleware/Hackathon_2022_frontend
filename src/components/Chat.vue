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
          <table class="table">
            <thead>
            <tr>
              <td>Title</td>
              <td>Description</td>
              <td></td>
            </tr>
            </thead>
            <tbody>
            <tr v-for="(item, index) in items" :key="item.title">
              <td><input type="text" id="title" class="form-control" v-model="item.title"></td>
              <td><input type="text" class="form-control" v-model="item.description"></td>
              <td>
                <a class="btn btn-success" v-on:click="addItem" v-if="items.length - 1 <= index" v-bind:class="{ disabled: item.title.length == 0 || item.description.length == 0 }">Add</a>
                <a class="btn btn-danger" v-on:click="removeItem(index);" v-if="(items.length - 1 >= index) && (items.length -1 != index)">Remove</a>
              </td>
            </tr>
            </tbody>
          </table>
        </v-card-text>
        <v-row>
<v-col class="col-10">
        <v-text-field
            align-center
            v-model="items.description"
            label="Regular"
        ></v-text-field>
</v-col>
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
      items: [
        {
          title: '',
          description: ''
        }
      ]
    }
  },
  methods: {
    addItem: function() {
      this.items.push({
        title: '',
        description: '',
      });
    },
    removeItem: function(index) {
      this.items.splice(index, 1);
    }
  }
};
</script>


<style scoped>

</style>