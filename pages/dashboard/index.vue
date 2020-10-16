<template>
  <v-container>
    <v-btn @click="send">send verification email</v-btn>
  </v-container>
</template>

<script>
export default {
  methods: {
    async send() {
      try {
        await this.$axios.$post('email/resend')
      } catch (e) {
        console.log(e)
      }
    },
  },
}
</script>
