<template>
  <div>
    <h3>Login</h3>
    <v-container>
      <v-row dense>
        <v-col cols="12">
          <v-btn @click="login()">
            Login via Keycloak
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'LoginVue',
  auth: 'guest',
  methods: {
    async login () {
      try {
        const response = await this.$auth.loginWith('keycloak')
        // eslint-ignore-next-line
        console.log(response)
      } catch (err) {
        // eslint-ignore-next-line
        console.log(err)
      }
    }
  }
}
</script>

<style scoped>

</style>
