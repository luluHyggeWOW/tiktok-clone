<template>
  <TopNav></TopNav>
  <div :class="route.fullPath ==='/'?'max-w-[1140px]':''" class="flex justify-between mx-auto w-full lg:px-2.5 px-0">
    <div>
      <SideNavMain></SideNavMain>
    </div>
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
let route = useRoute();
</script>

<style scoped>
</style>