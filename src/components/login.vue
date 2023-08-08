<script setup>
import {reactive, ref} from "vue";
import Dashboard from './Dashboard.vue'
const errorMsg = ref('')
const successMsg = ref(true)

const userData = reactive({
  username: '',
  password: ''
})

function loginRegData() {
  const localUsername = localStorage.getItem('username')
  const localPassword = localStorage.getItem('password')

  if (userData.username === localUsername && userData.password === localPassword) {
    successMsg.value = false
  } else {
    errorMsg.value = 'Error! Username or Password is not match'
  }
}
</script>

<template>
  <div class="" v-if="successMsg">
    <p class="mb-5 text-red-700" v-if="errorMsg">{{errorMsg}}</p>
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

    <div class="flex items-center justify-between">
      <button @click.prevent="loginRegData()"
              class="bg-orange-600 hover:bg-orange-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="button">
        Sign In
      </button>
    </div>
  </div>
  <Dashboard v-else />
</template>

<style scoped>

</style>
