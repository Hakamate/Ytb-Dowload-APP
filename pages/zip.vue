<template>
  <v-layout>
    <v-flex class="text-center">
      <form action>
        <input id="zip" type="file" webkitdirectory directory multiple />
      </form>
    </v-flex>
  </v-layout>
</template>

<script>

export default {
  components: {
  },
  mounted() {
    const zipInput = document.getElementById("zip");
    zipInput.onchange = function() {
      console.log(zipInput.file)
    };
  }
};
</script>
