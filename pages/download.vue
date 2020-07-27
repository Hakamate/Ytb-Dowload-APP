<template>
  <v-layout>
    <v-flex class="text-center">
      <h1 class="my-3">Convert Youtube to MP3</h1>
      <div class="d-flex justify-center">
        <v-text-field id="url-input" label="Youtube URL"></v-text-field>
        <v-btn id="convert-button" class="align-self-center ml-4" color="error"
          >Convert</v-btn
        >
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
// const downFileName='today'
// const extensionName='xlsx'
// const axiosConfig={
//   method: 'post',
//   url: 'http://127.0.0.1:3333/api/download',
// }

// import AxiosStream from "axios-stream";
import axios from "axios";
import { WritableStream } from "web-streams-polyfill/ponyfill";
import streamSaver from "streamsaver";

export default {
  components: {},
  mounted() {
    const urlInput = document.getElementById("url-input");
    const convertBtn = document.getElementById("convert-button");

    convertBtn.addEventListener("click", () => {
      console.log(`URL: ${urlInput.value}`);
      this.sendURL(urlInput.value);
    });
  },
  methods: {
    sendURL: function(url) {
      console.log(url);
      fetch("http://127.0.0.1:3333/api/download", {
        method: "POST",
        headers: {
          Accept: "application/json",
          "Content-Type": "application/json"
        },
        body: JSON.stringify({ URL: url })
      })
        .then(response => response.blob())
        .then(blob => {
          console.log(blob);
          var url = window.URL.createObjectURL(blob);
          var a = document.createElement("a");
          a.href = url;

          console.log(url);
          a.download = "music.mp3";
          document.body.appendChild(a); // we need to append the element to the dom -> otherwise it will not work in firefox
          a.click();
          a.remove(); //afterwards we remove the element again
        });
    }
  }
};
</script>
<style scoped>
#convert-button {
  transform: translateY(-3px);
}
</style>
