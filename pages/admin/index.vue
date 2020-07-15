<template>
  <v-row justify="center" align="center" class="fill-height">
    <v-col md="6">
      <v-card>
        <v-card-title class="headline pl-8">
          Login
        </v-card-title>
        <ValidationObserver v-slot="{ handleSubmit, reset }">
          <form
            ref="form"
            @submit.prevent="handleSubmit(login)"
            @reset.prevent="reset"
          >
            <v-card-text>
              <ValidationProvider
                v-slot="{ errors }"
                name="Email"
                rules="required|email"
              >
                <v-text-field
                  v-model="email"
                  :error-messages="errors"
                  label="Email"
                  solo
                ></v-text-field>
              </ValidationProvider>
              <ValidationProvider
                v-slot="{ errors }"
                name="Password"
                rules="required|min:5"
              >
                <v-text-field
                  v-model="password"
                  label="Password"
                  solo
                  :error-messages="errors"
                  :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
                  :type="showPassword ? 'text' : 'password'"
                  @click:append="showPassword = !showPassword"
                ></v-text-field>
              </ValidationProvider>
            </v-card-text>
            <v-card-actions class="pl-5 pb-5 flex justify-space-between">
              <v-btn type="submit" color="primary">Login</v-btn>
              <v-btn text small>Forgot Password?</v-btn>
            </v-card-actions>
          </form>
        </ValidationObserver>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      showPassword: false,
      password: '',
      email: ''
    }
  },
  methods: {
    login() {
      this.$router.push('/admin/dashboard')

      // this.$refs.form.setErrors({
      //       Email: ["We don't reconize, this email"],
      //       Password: ["We don't reconize, this password"]
      //     })
    }
  },
  head() {
    return {
      title: 'Admin Login'
    }
  }
}
</script>
