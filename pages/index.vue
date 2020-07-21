<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="text-center">
        <logo />
        <vuetify-logo />
      </div>
      <v-card>
        <v-card-title class="headline">
          Welcome to H-Tools, an Web App used to group NuxtApps
        </v-card-title>
        <v-card-text>
          <h2>Functionalities : </h2>
          <ul class="ma-3">
            <li>Convert Youtube to MP4</li>
          </ul>
          <div class="text-xs-right">
            <em><small>&mdash; Thomas CLEMENT (Hakamate)</small></em>
          </div>
          <hr class="my-3">
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
            rel="noopener noreferrer"
          >
            H-Tools GitHub
          </a>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/download"
          >
            Convert Ytb
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    Logo,
    VuetifyLogo
  }
}
</script>
