<template>
  <v-container dark>
    <v-row justify="center">
      <v-col cols="12" md="8" lg="6">
        <v-form
          ref="form"
          v-model="valid"
          class="mb-4"
          lazy-validation
          @submit.prevent="resetPassword"
        >
          <v-text-field
            v-model="form.email"
            :rules="[rules.required, rules.emailValid]"
            label="E-mail"
            required
            filled
          ></v-text-field>
          <v-text-field
            v-model="form.password"
            :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[
              rules.required,
              rules.passwordLength,
              rules.passwordLowerCase,
              rules.passwordUpperCase,
              rules.passwordSpecials,
              rules.passwordNumbers,
            ]"
            :type="show ? 'text' : 'password'"
            name="password"
            label="Password"
            filled
            required
            @click:append="show = !show"
          ></v-text-field>

          <v-text-field
            v-model="form.password_confirmation"
            :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[rules.required, rules.passwordMatch]"
            :type="show ? 'text' : 'password'"
            name="password_confirmation"
            label="Password confirmation"
            filled
            required
            @click:append="show = !show"
          ></v-text-field>

          <div class="d-flex justify-center">
            <v-btn
              type="submit"
              :disabled="!valid"
              color="primary"
              class="mr-4"
              @click="validate"
            >
              Reset password
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
      show: false,
      form: {
        email: '',
        password: '',
        password_confirmation: '',
      },
    }
  },
  methods: {
    validate() {
      this.$refs.form.validate()
    },
    async resetPassword() {
      try {
        await this.$axios.post('/password/reset', {
          token: this.$route.params.token,
          email: this.form.email,
          password: this.form.password,
          password_confirmation: this.form.password_confirmation,
        })
        // success notification
        // redirection
        // this.$router.push({
        //   name: 'auth-signin',
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
