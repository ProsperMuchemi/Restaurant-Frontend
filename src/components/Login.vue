<template>
    <div>
      <v-img class="mx-auto my-6" max-width="228" src="../logo.png" ></v-img>
  
      <v-card class="mx-auto pa-12 pb-8" elevation="8" max-width="448" rounded="lg" >
        <div class="text-subtitle-1 text-medium-emphasis">Account</div>
  
        <v-text-field density="compact" placeholder="Email address" prepend-inner-icon="mdi-email-outline" variant="outlined"  v-model="login_info.email"></v-text-field>
  
        <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
          Password
          <a class="text-caption text-decoration-none text-blue" href="#" rel="noopener noreferrer" target="_blank" > Forgot login password?</a>
        </div>
  
        <v-text-field
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          placeholder="Enter your password"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="visible = !visible"
          v-model="login_info.password"
        ></v-text-field>
  
        <v-btn class="mb-8" color="warning" size="large" variant="tonal" block  @click="login()" > Log In </v-btn>
  
        <v-card-text class="text-center">
          <a class="text-blue text-decoration-none" href="/register" rel="noopener noreferrer" >
            Sign up now <v-icon icon="mdi-chevron-right"></v-icon>
          </a>
        </v-card-text>
      </v-card>
    </div>
</template>
<script setup>
import { ref } from "vue";
import axios from 'axios'

const visible = ref(false)
const login_info = ref({
  email:null,
  password: null
})

function login(){
  axios
    .post('http://127.0.0.1:8000/api/login', login_info.value)
    .then((response) => {
    //redirect to home
      console.log(response),
      window.location.href = 'home'
})
}

</script>