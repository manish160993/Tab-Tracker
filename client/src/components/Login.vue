<template>
<v-layout justify-center>
    <v-flex xs6>
        <div class="white elevation-2">
            <v-toolbar flat dense class="cyan" dark>
                <v-toolbar-title>Login</v-toolbar-title>
            </v-toolbar>
            <div class="pl-4 pr-4 pt-2 pb-2">
                <form name="tab-tracker-form" autocomplete="off">
                <v-text-field label="Email" v-model="email"></v-text-field><br>
                <v-text-field label="Password" autocomplete="new-password" type="password" v-model="password"></v-text-field><br>
                <br><br>             
                </form>
                <div class="error" v-html="error"></div>
                <div class="success" v-html="success"></div>
                <v-btn dark class="cyan" @click="login">Login</v-btn>
            </div>
        </div>
    </v-flex>
</v-layout>
</template>

<script>
import AuthenticationService from './../services/AuthenticationService'
export default {
  data () {
    return {
        email: "",
        password: "",
        error: null,
        success: null
    }
  },
  methods:{
      async login(){
          try{
              this.success=null;
              this.error=null;
            const response = await AuthenticationService.login({
                email: this.email,
                password: this.password

            })
            this.$store.dispatch('setToken', response.data.token)
            this.$store.dispatch('setUser',response.data.user)
            this.success="You have successfully logged in"
          }catch(error){
              this.error = error.response.data.error;
          }
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error{
    color:red
}

</style>
