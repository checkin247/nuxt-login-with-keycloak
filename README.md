# Nuxt login with Keycloak
Example nuxt setup to proof the concept of authorization code flow with proof key for code exchange with keycloak.

By the time of this writing (2020-11-15), the setup requires auth-next with version 5.
Check what [version](https://github.com/nuxt-community/auth-module) the master has and modify accordingly.

Step by step [instructions to implement in your own project can be found here](https://tliebrand.com/19-programming/26-how-to-authorize-nuxt-against-keycloak)
## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

## Authentication
The login will be handled on the keycloak server with a redirect.
Once successfully authenticated, the user will be redirected the home page.
We can [enforce access to content through a middleware](https://auth.nuxtjs.org/guide/middleware.html).
The intended use case is that we use the supplied credentials (access token) which are saved in a cookie to request protected API resources.

Navigate to /login
Once successfully logged in, you can access the user object from the vuex store like so:

```
this.$auth.user
```

One could for instance set the user in the mounted method on the template to display a user menu

```
export default {
  mounted () {
    this.user = this.$auth.user !== null ? this.$auth.user : this.user
  }
}
```
### Configuration
Update the realm in the endpoints path in the auth strategy.
Change the clientId to match the client on your keycloak realm.
