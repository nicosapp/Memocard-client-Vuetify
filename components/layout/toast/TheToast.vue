<template>
  <component :is="component" />
</template>

<script>
import ToastDefault from '@/components/layout/toast/ToastDefault'
import { mapGetters } from 'vuex'
export default {
  components: {
    ToastDefault,
  },
  computed: {
    ...mapGetters({
      component: 'toast/component',
    }),
  },
}
</script>
