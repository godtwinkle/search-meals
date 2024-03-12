<script setup></script>

<template>
  <div class="bg-gray-100 h-full">
    <header class="bg-white shadow h-16 flex justify-between items-stretch">
      <router-link :to="{ name: 'home' }"> Trang chủ </router-link>
      <div>
        <router-link to="/" class="px-2 h-full hover:bg-purple-200">
          Tìm kiếm món ăn
        </router-link>
        <router-link to="/" class="px-2 h-full hover:bg-purple-200">
          Món ăn theo chữ cái
        </router-link>
        <router-link to="/" class="px-2 h-full hover:bg-purple-200">
          Món ăn theo thành phần
        </router-link>
      </div>
    </header>
  </div>
  <main>
    <router-view />
  </main>
</template>

<style scoped></style>
