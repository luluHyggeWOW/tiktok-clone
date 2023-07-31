<template>
  <div @mouseenter="isHover(true)" @mouseleave="isHover(false)"
    class=" relative brightness-90 hover:brightness-[1.1] cursor-pointer">
    <div v-if="!isLoaded"
      class="flex absolute items-center justify-center top-0 left-0 aspect-[3/4] w-full object-cover rounded-md bg-black">
      <Icon class=" animate-spin ml-1" name="mingcute:loading-line" size="100" color="#FFFFFF"></Icon>
    </div>
    <div>
      <video ref="video" muted loop class="aspect-[3/4] object-cover rounded-md"
        src="https://video.699pic.com/videos/13/50/40/b_QEu7qXbWj4rg1672135040.mp4"></video>
    </div>
    <div class="px-1">
      <div class="text-gray-700 text-[15px] pt-1 break-words">This is some text</div>
      <div class="flex items-center -ml-1 text-gray-600 font-bold text-xs">
        <Icon name="gg:loadbar-sound" size="20"></Icon>
        3%
        <Icon class="ml-1" name="tabler:alert-circle" size="16"></Icon>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps(['post'])
const route = useRoute()
const router = useRouter()
let video = ref(null)
let isLoaded = ref(false)
const isHover = async (bool) => {
  if (bool) video.value.play()
  else video.value.pause()
}
onMounted(async () => {
  if (video.value) {
    isLoaded.value = true
    await video.value.addEventListener('loadeddata', (e) => {
      console.log(22, e);
      if (e.target) {
        console.log(33, e.target);
        setTimeout(() => {
          isLoaded.value = true
        }, 200);
      }
    })
  }
})
onBeforeUnmount(() => {
  video.value.pause()
  video.value.currentTime = 0
  video.value.src = ''
})
</script>

