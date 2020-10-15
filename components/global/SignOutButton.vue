<template>
  <v-btn @click.prevent="signOut">
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
