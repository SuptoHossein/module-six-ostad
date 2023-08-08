<script setup>
const localUsername = localStorage.getItem('username')
</script>

<template>
  <section class="mx-auto container">
    <div class="bg-gray-300 px-5 py-5">
      <h1 class="text-purple-700 text-2xl"><strong>Welcome! </strong>{{localUsername}} You are Loggedin</h1>
    </div>
  </section>
</template>

<style scoped>

</style>
