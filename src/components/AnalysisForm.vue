<template>
  <v-app>
    <v-main class="blue lighten-3">
      <v-container>
        <v-row>
          <v-col cols="4">
            <v-sheet
                    class="pa-4 text-center"
                    elevation="4"
                    rounded="lg"
                    min-height="20vh"
            >
              <v-text-field
                      label="Text goes here..."
                      placeholder="I love you!"
                      outlined
                      v-model="message"
              >
              </v-text-field>
              
              <v-divider class="my-2"></v-divider>

              <v-btn
                      color="success"
                      elevation="4"
                      rounded
                      v-on:click="analyseText(message)">Send :)
              </v-btn>
            </v-sheet>
          </v-col>

          <v-col xs="6">
            <v-sheet
                    class="pa-4"
                    elevation="4"
                    min-height="70vh"
                    rounded="lg"
            >
<!--              <v-img-->
<!--                      max-height="150"-->
<!--                      max-width="250"-->
<!--                      src="../../src/assets/images/sad_happy_masks.png"-->
<!--              ></v-img>-->
              <div>{{ result }}</div>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
  import {endpoint_address} from "@/utils";

  const axios = require("axios");

  export default {
  name: 'AnalysisForm',
  data: () => ({
    message: "",
    result: ""
  }),
  methods: {
    async analyseText(message) {
      try {
        await axios.get(`${endpoint_address}/classify`, {
          params: {
            message: message.toString()
          }
        }).then(response => {
          console.log(response);
          if (response && response.status === 200) {
            this.result = response.data;
          }
        })
      } catch (e) {
        console.error(e);
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
