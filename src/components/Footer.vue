<template>
  <v-footer
    dark
    padless
    app
  >
    <v-card
      class="flex"
      flat
      tile
    >
      <v-card-text class="py-2 white--text text-center">
        &copy; {{ new Date().getFullYear() }} — <strong>diprojectin.com</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
  export default {
    data: () => ({

    }),
  }
</script>