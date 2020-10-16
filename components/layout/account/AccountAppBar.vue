<template>
  <v-app-bar :clipped-left="false" fixed app color="primary">
    <!-- MIDDLE -->
    <v-spacer />
    <v-toolbar-title>Your Profile</v-toolbar-title>
    <v-spacer />
    <!-- MIDDLE -->
    <SignOutButton color="primaryText">
      <v-icon>mdi-logout-variant</v-icon>
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
