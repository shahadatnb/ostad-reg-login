<script setup>
import { ref, reactive } from 'vue'

const users = ref([])

const registerForm = reactive({
  email: '',
  password: ''
})

const loginForm = reactive({
  email: '',
  password: ''
})

const register = () => {
  if(registerForm.email == '') {
    alert('Email is required');
  }else if(registerForm.password == '') {
    alert('Password is required');
  }else{
    users.value.push(registerForm)
    formStatus.logedIn = false
    formStatus.register = false
    formStatus.login = true
  }
  
}

const login = () => {
  if(loginForm.email == '') {
    alert('Email is required');
  }else if(loginForm.password == '') {
    alert('Password is required');
  }else{
    const foundUser = users.value.find(item => item.email == loginForm.email && item.password == loginForm.password);
    if(foundUser){
      formStatus.logedIn = true
      formStatus.register = false
      formStatus.login = false
    }
    else{
      alert('User or password is incorrect');
    }
  }
}

const formStatus = reactive({
  login: false,
  register: true,
  logedIn: false
})

</script>

<template>
<div class="container">
  <div v-if="formStatus.register == true" class="bg-white shadow-md rounded-md p-6 w-6/12">
      <h2 class="text-2xl font-bold mb-4">Registration</h2>
      <form @submit.prevent="register">
        <div class="mb-4">
          <label for="email" class="block font-medium">Email:</label>
          <input type="email" id="email" v-model="registerForm.email" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-gray-600  border-solid rounded-md border-gray-300 focus:border-indigo-500 focus:ring">
        </div>
        <div class="mb-4">
          <label for="password" class="block font-medium">Password:</label>
          <input type="password" id="password" v-model="registerForm.password" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-gray-600  border-solid rounded-md border-gray-300 focus:border-indigo-500 focus:ring">
        </div>
        <button type="submit" class="w-full bg-indigo-500 text-white font-bold py-2 px-4 rounded-md">Register</button>
      </form>
    </div>
    <div class="mx-4"></div>
    <div v-if="formStatus.login == true" class="bg-white shadow-md rounded-md p-6 w-6/12">
      <h2 class="text-2xl font-bold mb-4">Login</h2>
      <form @submit.prevent="login">
        <div class="mb-4">
          <label for="email" class="block font-medium">Email:</label>
          <input type="email" id="email" v-model="loginForm.email" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-gray-600  border-solid rounded-md border-gray-300 focus:border-indigo-500 focus:ring">
        </div>
        <div class="mb-4">
          <label for="password" class="block font-medium">Password:</label>
          <input type="password" id="password" v-model="loginForm.password" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:border-gray-600  border-solid rounded-md border-gray-300 focus:border-indigo-500 focus:ring">
        </div>
        <button type="submit" class="w-full bg-indigo-500 text-white font-bold py-2 px-4 rounded-md">Login</button>
      </form>
    </div>

    <div v-if="formStatus.logedIn == true" class="bg-white shadow-md rounded-md p-6">
      <h2 class="text-2xl font-bold mb-4">You are logged in</h2>
    </div>
</div>
</template>

<style scoped>

</style>
