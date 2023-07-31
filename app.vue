<template>
  <NuxtPage></NuxtPage>
  <AuthOverlay v-if="isLoginOpen"></AuthOverlay>
  <EditProfileOverlay></EditProfileOverlay>
</template>
<script setup>
import { storeToRefs } from 'pinia'
const { $generalStore } = useNuxtApp()
const { isLoginOpen, isEditProfileOpen } = storeToRefs($generalStore)
</script>
