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
import axios from 'axios';

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
  methods:{
    sendURL: async function(url){
      console.log(url)
      await axios.post(`http://127.0.0.1:3333/api/download`, {params:{URL:url}})
        .catch(error => {
          console.log(error);
        })
        .then(response => console.log(response))
    }
  }
};
</script>
<style  scoped>

#convert-button {
  transform: translateY(-3px);
}

</style>