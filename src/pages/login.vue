<template>
  <v-container fluid>
    <v-row class="text-center">
      <v-col cols="3" md="3" sm="2" />
      <v-col cols="12" md="6" sm="8">
        <v-card class="pt-10" elevation="11">
          <h2 class="purple--text text-uppercase">로그인 페이지</h2>
          <v-divider class="mt-2" color="purple" />
          <v-form
            ref="form"
            v-model="valid"
            class="mt-10 mb-6 pr-8 pl-8 pb-8 pt-4"
            lazy-validation
            @submit.prevent="onLogin"
          >
            <v-text-field
              v-model="email"
              append-icon="mail_outline"
              color="purple"
              error-count="2"
              label="E-mail"
              outlined
              required
              :rules="emailRules"
            />
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              color="purple"
              label="Password"
              outlined.
              required
              :rules="passwordRules"
              :type="show1 ? 'text' : 'password'"
              @click:append="show1 = !show1"
            />

            <v-btn
              block
              class="mr-4 text"
              color="purple darken-4"
              :disabled="!valid"
              type="submit"
              x-large
              @click="validate"
            >
              <span class="white--text">Login</span>
              <v-icon light>cached</v-icon>
            </v-btn>
          </v-form>
        </v-card>
      </v-col>
      <v-col cols="3" md="3" sm="2" />
    </v-row>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        show1: false,
        valid: true,
        emailRules: [
          (v) => !!v || 'E-mail is required',
          (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        passwordRules: [
          (v) => !!v || 'Password is required',
          (v) => v.length >= 8 || 'Password must be at least 8 characters',
        ],
      }
    },
    methods: {
      onLogin() {
        if (this.$refs.form.validate()) {
          this.$store.dispatch('login', {
            email: this.email,
            password: this.password,
          })
        }
      },
    },
  }
</script>
