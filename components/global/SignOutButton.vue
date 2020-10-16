<template>
  <v-btn icon @click.prevent="signOut">
    <slot />
  </v-btn>
</template>

<script>
export default {
  methods: {
    async signOut() {
      await this.$auth.logout()
    },
  },
}
</script>
