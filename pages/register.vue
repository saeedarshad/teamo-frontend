<template>
  <section class="section">
    <div class="container">
      <div class="columns">
        <div class="column is-4 is-offset-4">
          <h2 class="title has-text-centered">Sign Up</h2>

          <Notification :message="error" :notifClass="notifClass" v-if="error"/>
          <Notification :message="success" :notifClass="notifClass" v-if="success"/>

          <form v-if="!success" method="post" @submit.prevent="register">
            <div class="field">
              <label class="label">Name</label>
              <div class="control">
                <input
                  type="text"
                  class="input"
                  name="name"
                  v-model="name"
                  required
                />
              </div>
            </div>
            <div class="field">
              <label class="label">User Name</label>
              <div class="control">
                <input
                  type="text"
                  class="input"
                  name="username"
                  v-model="username"
                  required
                />
              </div>
            </div>
            <div class="field">
              <label class="label">Email</label>
              <div class="control">
                <input
                  type="email"
                  class="input"
                  name="email"
                  v-model="email"
                  required
                />
              </div>
            </div>
            <div class="field">
              <label class="label">Password</label>
              <div class="control">
                <input
                  type="password"
                  class="input"
                  name="password"
                  v-model="password"
                  required
                />
              </div>
            </div>
            <div class="control">
              <button type="submit" class="button is-dark is-fullwidth">Register</button>
            </div>
          </form>

          <div v-if="success">
            Go to <nuxt-link to="/login">Sign In</nuxt-link>
          </div>

          <div v-if="!success" class="has-text-centered" style="margin-top: 20px">
            Already got an account? <nuxt-link to="/login">Sign In</nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Notification from '~/components/Notification'

export default {
  middleware: 'guest',
  components: {
    Notification,
  },

  data() {
    return {
      name: '',
      username: '',
      email: '',
      password: '',
      error: null,
      success: null,
      notifClass: null,
    };
  },

  methods: {
    async register() {
      try {
         await this.$axios.post('register', {
          name: this.name,
          username: this.username,
          email: this.email,
          password: this.password
        });

        this.success = 'User created successfully';
        this.notifClass = 'is-success';

      } catch (e) {
        this.notifClass = 'is-danger';
        this.error = e?.response?.data?.error || 'Internal Server Error';
      }
    }
  }
}
</script>