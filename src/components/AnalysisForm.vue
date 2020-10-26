<template>
  <div class="hello">
    <input v-model="message" placeholder="Text goes here...">
    <button v-on:click="analyseText(message)">Send :)</button>
    <div>{{ result }}</div>
  </div>
</template>

<script>
  import {endpoint_address} from "@/utils";

  const axios = require("axios");

  export default {
  name: 'AnalysisForm',
  data() {
    return {
      message: "",
      result: ""
    };
  },
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
