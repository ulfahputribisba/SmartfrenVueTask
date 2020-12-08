<template>
  <q-page>
   <div class="q-pa-md q-mt-xl">

    <div class="row">
      <div class="col"></div>
      <div class="col-6">
        <div class="text-h4 flex flex-center q-mb-md">Sign In</div>
        <q-form
        @submit="onSubmit"
          class="q-gutter-md q-mt-lg"
        >
          <q-input
            filled
            v-model="username"
            label="Username"
            lazy-rules
            :rules="[ val => val && val.length > 0 || 'Please type something']"
          />

          <q-input
            filled
            v-model="password"
            type="password"
            label="Password"
            lazy-rules
            :rules="[
              val => val !== null && val !== '' || 'Please type your password'
            ]"
          />
          <div class="flex flex-center">
            <q-btn label="Login" type="submit" color="primary"/>
          </div>
        </q-form>
      </div>
      <div class="col"></div>
    </div>
  </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      username: null,
      password: null
    }
  },
  methods: {
    onSubmit () {
      if (this.username === null && this.password === null) {
        this.$q.notify({
          color: 'red-5',
          textColor: 'white',
          icon: 'warning',
          message: 'You need to complete the form!'
        })
      }
      if (this.username !== null && this.password !== null) {
        this.$q.notify({
          color: 'green',
          textColor: 'white',
          icon: 'cloud-done',
          message: 'Login Success'
        })
        this.$router.push('/todo')
      }
    }
  }
}
</script>
