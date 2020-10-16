<template>
  <v-container> Account </v-container>
</template>

<script>
export default {
  layout: 'account',
  middleware: ['isAuth'],
}
</script>
