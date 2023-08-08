<script setup>

import Register from "./components/register.vue";
import Login from "./components/login.vue";
import {reactive, ref} from "vue";

const isLoginForm = ref(false)

function changeMessage() {
  return isLoginForm.value =! isLoginForm.value
}


</script>

<template>
  <section class="flex h-screen w-full">
    <div class="w-1/2"
         style="background-image: url(https://images.unsplash.com/photo-1690555575753-7aa27df96b52?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=774&q=80); background-repeat: no-repeat; background-size: cover;">
      <h1 class="mb-5 text-2xl mt-10 ml-10 text-white">Kosmos!</h1>
    </div>

    <div class="w-1/2 flex flex-col justify-center items-center bg-gray-200">
      <h2 class="mb-5 text-xl">{{ isLoginForm==false ? 'Register' : 'Login' }}</h2>
      <div class="w-full max-w-xs">

        <div class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
          <login v-if="isLoginForm"/>

          <register v-else/>

          <a @click.prevent="changeMessage()"
             class="mt-5 inline-block align-baseline font-bold text-sm text-orange-600 hover:text-orange-800" href="#">
            Or {{ isLoginForm==false ? 'Login' : 'Register' }}
          </a>
        </div>

        <p class="text-center text-gray-500 text-xs">
          &copy;2023 Acme Corp. All rights reserved.
        </p>
      </div>
    </div>
  </section>


</template>

