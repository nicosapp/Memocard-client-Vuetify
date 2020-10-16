<template>
  <v-container dark>
    <v-row justify="center">
      <v-col cols="12" md="8" lg="6">
        <div class="text-center mb-8">Send me a link by email!</div>
        <v-form
          ref="form"
          v-model="valid"
          class="mb-4"
          lazy-validation
          @submit.prevent="sendResetEmail"
        >
          <v-text-field
            v-model="form.email"
            :rules="[rules.required, rules.emailValid]"
            label="E-mail"
            required
            filled
          ></v-text-field>

          <div class="d-flex justify-center">
            <v-btn
              type="submit"
              :disabled="!valid"
              color="primary"
              class="mr-4"
              @click="validate"
            >
              Send email
            </v-btn>
          </div>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import validationRules from '@/mixins/helper/formValidationRules'
export default {
  mixins: [validationRules],
  data() {
    return {
      valid: true,
      form: {
        email: '',
      },
    }
  },
  methods: {
    validate() {
      this.$refs.form.validate()
    },
    async sendResetEmail() {
      try {
        await this.$axios.post('/password/email', { email: this.form.email })
        // this.$notifier.success({
        //   text: 'The email sent successfully!',
        // })
      } catch (e) {
        if (e.response && e.response.status === 422) {
          this.validation = e.response.data.errors
          // this.$notifier.error({ text: 'There is an error in the form' })
        }
      }
    },
  },
}
</script>
