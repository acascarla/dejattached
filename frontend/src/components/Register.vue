<template>
  <div>
    <h4>Register</h4>
    <form @submit.prevent='register'>
      <label for='username'>Username</label>
      <div>
				<input id='username' type='text' v-model='username' required autofocus>
      </div>
      <label for='password'>Password</label>
      <div>
				<input id='password' type='password' v-model='password' required>
      </div>
      <label for='password-confirm'>Confirm Password</label>
      <div>
				<input id='password-confirm' type='password' v-model='password_confirmation' required>
      </div>
      <div>
				<button type='submit'>Register</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        username : '',
        password : '',
        password_confirmation : '',
        is_admin : null
      }
    },
    methods: {
      register: function () {
        let data = {
          username: this.username,
          password: this.password,
          is_admin: this.is_admin
        }
        this.$store.dispatch('register', data)
					.then(() => this.$router.push('/'))
      }
    }
  }
</script>
