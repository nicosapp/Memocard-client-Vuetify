<template>
  <v-app-bar :clipped-left="false" fixed app color="primary">
    <!-- MIDDLE -->
    <v-spacer />
    <v-toolbar-title class="primaryText--text font-title">
      Your Profile
    </v-toolbar-title>
    <v-spacer />
    <!-- MIDDLE -->
    <SignOutButton>
      <v-icon color="primaryText">mdi-logout-variant</v-icon>
    </SignOutButton>
  </v-app-bar>
</template>

<script>
import SignOutButton from '@/components/global/SignOutButton'
export default {
  components: {
    SignOutButton,
  },
}
</script>
