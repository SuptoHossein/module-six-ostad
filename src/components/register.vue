<script setup>

import { reactive, ref } from "vue";

const errorMsg = ref("")
const successMsg = ref("")

const userData = reactive({
  username: "",
  password: "",
  confirmPassword: ""
})

function storeRegData() {
  localStorage.clear();
  if (userData.username !== '') {
    if (userData.password === userData.confirmPassword) {
      errorMsg.value = ""
      localStorage.setItem('username', userData.username)
      localStorage.setItem('password', userData.password)
      successMsg.value = "Registration successful"
    } else {
      successMsg.value = ""
      errorMsg.value = "Password and Confirm Password is not Match"
    }
  } else {
    successMsg.value = ""
    errorMsg.value = "Please fill the input box"
  }
}
</script>

<template>
  <p class="mb-5 text-red-700" v-if="errorMsg">{{ errorMsg }}</p>
  <p class="mb-5 text-green-700" v-else>{{ successMsg }}</p>
  <!--  {{errorMsg}}-->
  <!--  {{successMsg}}-->
  <div class="mb-4">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
      Username
    </label>
    <input v-model="userData.username"
      class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
      id="username" type="text" placeholder="Username">
  </div>
  <div class="mb-6">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
      Password
    </label>
    <input v-model="userData.password"
      class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
      id="password" type="password" placeholder="******************">
    <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
  </div>
  <div class="mb-6">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
      Confirm Password
    </label>
    <input v-model="userData.confirmPassword"
      class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
      id="password" type="password" placeholder="******************">
    <!-- <p class="text-red-500 text-xs italic">Please choose a password.</p> -->
  </div>

  <div class="flex items-center justify-between">
    <button @click.prevent="storeRegData()"
      class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
      type="button">
      Register
    </button>
  </div>
</template>

<style scoped></style>
