<template>
  <div class="login">
    <v-sheet class="hidden-xs-only d-flex justify-center align-center" height="920">
      <v-card class="text-center" height="650" width="470" elevation="4">
        <img alt="Trade Track logo" src="../../assets/logo.png" width="250" height="250">
        <v-card class="text-center" flat>
          <h4>Log in with:</h4>
          <v-btn icon>
            <v-icon dark>mdi-facebook</v-icon>
          </v-btn>
          <v-btn icon>
            <v-icon dark>mdi-google</v-icon>
          </v-btn>
        </v-card>
        <v-divider class="mx-15"></v-divider>
        <v-card-text>
          <h4>Or log in with credentials:</h4>
          <v-form >
            <v-text-field v-model="email" :rules="emailRules" label="Email" prepend-inner-icon="mdi-account-outline" required></v-text-field>
            <v-text-field v-model="password" :rules="passwordRules" label="Password" prepend-inner-icon="mdi-lock-outline"
              :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'" :passwordRules="[passwordRules.required, passwordRules.min]"
              :type="showPassword ? 'text' : 'password'" @click:append="showPassword = !showPassword" required @keyup.enter="login"
            ></v-text-field>
            <div class="pt-4">
              <v-btn class="pa-5" @click="login" color="light-green darken-3" rounded dark>
              <!-- <v-btn class="pa-5" to="/dashboard" color="blue accent-4" rounded dark> -->
                <h4>Login</h4>
              </v-btn>
            </div>
            <div class="pt-5">
              <v-btn to="/forgot-password" color="light-green darken-3" rounded text>Forgot Your Password?</v-btn> <br>
              <!-- <p>Don't have an account? <v-btn to="/register" color="#1956B4" text>Register</v-btn></p> -->
            </div>
          </v-form>
        </v-card-text>
      </v-card>
    </v-sheet>
  </div>
</template>

<script>
//import axios from 'axios'

export default {
  name: 'Login',
  data () {
    return {
      email: '',
      password: '',
      showPassword: false,
      emailRules: [
        v => !!v || 'Email is required',
        v => (v && v.length <= 50) || 'Email must be less than 50 characters',
      ],
      passwordRules: [
        v => !!v || 'Password is required',
        // v => (v && v.length <= 8) || 'Password must be less than 8 characters',
        // () => (`The email and password you entered don't match`),
      ]
    }
  },
  methods: {
    async login() {
      // const response = await axios.post('tenants/login', {
      //   email: this.email,
      //   password: this.password
      // })

      // localStorage.setItem('token', response.data.token)
      this.$router.push('/dashboard')
    }
  }
}
</script>
