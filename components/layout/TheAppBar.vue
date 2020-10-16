<template>
  <v-app-bar :clipped-left="false" fixed app color="primary">
    <!-- MIDDLE -->
    <v-spacer />
    <v-img
      class="mr-3"
      max-height="60px"
      contain
      :src="require('~/assets/logo.svg')"
    ></v-img>
    <v-spacer />
    <!-- MIDDLE -->
    <v-btn
      v-if="!$auth.loggedIn && isHomePage"
      color="primaryText"
      icon
      nuxt
      to="/auth/signin"
    >
      <v-icon>mdi-login-variant</v-icon>
    </v-btn>
    <v-btn
      v-if="$auth.loggedIn && isHomePage"
      color="primaryText"
      icon
      nuxt
      to="timeline"
    >
      <v-icon>mdi-format-list-text</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  props: {
    page: {
      required: false,
      type: String,
      default: '',
    },
  },
  data() {
    return {}
  },
  computed: {
    ...mapGetters({
      drawerLeft: 'drawerLeft/value',
    }),
    logo() {
      return '~/assets/logo.svg'
    },
    title() {
      switch (this.page) {
        case 'account':
          return 'Your profile'
        default:
          return 'MyCodeSnippets'
      }
    },
    isSigninPage() {
      return this.$route.path.indexOf('signin') > 0
    },
    isAccountPage() {
      return this.$route.path.indexOf('account') > 0
    },
    isHomePage() {
      return this.$route.path.length === 1
    },
  },
  methods: {
    ...mapActions({
      setDrawerLeft: 'drawerLeft/setValue',
    }),
    toggleLeft() {
      this.setDrawerLeft(!this.drawerLeft)
    },
  },
}
</script>
