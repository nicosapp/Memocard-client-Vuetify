<template>
  <v-container>
    TEMPLATE
    <div>
      <v-btn @click="toast">TOAST</v-btn>
    </div>
  </v-container>
</template>

<script>
export default {
  mounted() {
    this.$store.dispatch('bottomBar/setActive', 'timeline')
  },
  methods: {
    toast() {
      // this.$notifier.success({ message: 'Test' })
      // this.$notifier.warn({ message: 'Test' })
      // this.$notifier.error({ message: 'Test' })
      // this.$notifier.info({ message: 'Test' })
    },
  },
}
</script>
