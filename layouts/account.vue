<template>
  <v-app dark>
    <AccountAppBar />
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
    <TheBottomBar />
    <TheFixedComponents />
  </v-app>
</template>

<script>
import AccountAppBar from '@/components/layout/account/AccountAppBar'
export default {
  components: {
    AccountAppBar,
  },
}
</script>
