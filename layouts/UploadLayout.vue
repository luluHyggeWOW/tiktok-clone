<template>

  <div class=" bg-[#F8F8F8] h-[100vh]">
    <TopNav></TopNav>
    <div class="flex justify-between mx-auto px-2 max-w-[1140px]">
      <slot></slot>
    </div>
  </div>
</template>

<script setup lang="ts">
let route = useRoute();
</script>

<style scoped>
</style>