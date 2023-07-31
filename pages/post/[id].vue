<template>
  <div id="PostPage"
    class="flexd lg:flex justify-between z-50 top-0 left-0 w-full h-full bg-black lg:overflow-hidden overflow-auto">
    <div class="lg:w-[calc(100%-540px)] h-full relative">
      <NuxtLink class=" absolute z-20 m-5 rounded-full bg-gray-700 p-1.5 hover:bg-gray-800">
        <Icon name="material-symbols:close" color="#ffffff" size="27"></Icon>
      </NuxtLink>
      <div v-if="true">
        <button :disabled="!isLoaded" @click="$event=>loopThroughPostsUp()"
          class=" absolute z-20 right-4 top-4 flex items-center justify-center rounded-full bg-gray-700 p-1.5 hover:bg-gray-800">
          <Icon name="mdi:chevron-up" size="30" color="#ffffff"></Icon>
        </button>
        <button :disabled="!isLoaded" @click="$event=>loopThroughPostsDown()"
          class=" absolute z-20 right-4 top-20 flex items-center justify-center rounded-full bg-gray-700 p-1.5 hover:bg-gray-800">
          <Icon name="mdi:chevron-down" size="30" color="#ffffff"></Icon>
        </button>
      </div>
      <img class=" absolute top-[18px] left-[70px] z-[2] rounded-full lg:mx-0 mx-auto" width="45"
        src="~/assets/images/tiktok-logo-small.png" alt="">
      <video v-if="!isLoaded" class="display  absolute object-cover w-full my-auto z-[0] h-screen"
        src="https://video.699pic.com/videos/13/50/40/b_QEu7qXbWj4rg1672135040.mp4"></video>
      <div v-if="!isLoaded" class="flex items-center justify-center bg-black bg-opacity-70 h-screen lg:min-w-[480px]:">
        <Icon class=" animate-spin ml-1" name="mingcute:loading-line" size="100" color="#ffffff"></Icon>
      </div>
      <div class=" bg-black bg-opacity-70 lg:min-w-[480px]">
        <video ref="video" v-if="true" loop muted class="h-screen w-full"
          src="https://video.699pic.com/videos/13/50/40/b_QEu7qXbWj4rg1672135040.mp4"></video>
      </div>
    </div>
    <div id="InfoSection" v-if="true" class=" lg:max-w-[550px]  relative w-full h-full bg-white">
      <div class="py-7"></div>
      <div class="flex items-center justify-between px-8">
        <div class="flex items-center">
          <NuxtLink href="/">
            <img class=" rounded-full lg:mx-0 mx-auto" width="40" src="https://picsum.photos/id/8/300/320" alt="">
          </NuxtLink>
          <div class="ml-3 pt-0.5">
            <div class="text-[17px] font-semibold">User name</div>
            <div class="text-[13px] -mt-5 font-light">User name
              <span class=" relative -top-[2px] text-[30px] pr-0.5">.</span>
              <span class=" font-medium">Data here</span>
            </div>
          </div>
        </div>
        <Icon v-if="true" @click="$event=>deletePost()" class=" cursor-pointer"
          name="material-symbols:delete-outline-sharp" size="25">
        </Icon>
      </div>
      <div class="px-8 mt-4 text-sm">This is the post text</div>
      <div class="px-8 mt-4 text-sm font-bold">
        <Icon name="mdi:music" size="17"></Icon>
        original sound - User name
      </div>
      <div class="flex items-center px-8 mt-8">
        <div class="pb-4 text-center flex items-center">
          <button class=" rounded-full bg-gray-200 p-2 cursor-pointer">
            <Icon name="mdi:heart" size="25"></Icon>
          </button>
          <span class="text-xs pl-2 pr-4 text-gray-800 font-semibold">123</span>
        </div>
        <div class="pb-4 text-center flex items-center">
          <button class=" rounded-full bg-gray-200 p-2 cursor-pointer">
            <Icon name="bx:bxs-message-rounded-dots" size="25"></Icon>
          </button>
          <span class="text-xs pl-2 pr-4 text-gray-800 font-semibold">123</span>
        </div>
      </div>
      <div id="Comments" class=" bg-[#f8f8f8] z-0 w-full h-[calc(100%-273px)] border-t-2 overflow-auto">
        <div class="pt-2"></div>
        <div v-if="false" class=" text-center mt-6 text-xl text-gray-500">No comments...</div>
        <div v-else class="flex items-center justify-between px-8 mt-4 ">
          <div class="flex items-center relative w-full ">
            <NuxtLink to="/">
              <img class=" absolute top-0 rounded-full lg:mx-0 mx-auto" width="40"
                src="https://picsum.photos/id/8/300/320">
            </NuxtLink>
            <div class="ml-14 pt-0.5 w-full">
              <div class="text-[18px] font-semibold flex items-center justify-between">
                User name
                <Icon v-if="true" @click="$event=>deleteComment()" class=" cursor-pointer"
                  name="material-symbols:delete-outline-sharp" size="25"></Icon>
              </div>
              <div class="text-[15px] font-light">
                Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                Doloremque aliquam ratione maxime dolorem
                facere beatae yoluptatum magni error, nam fugiat doloribus,
                repellendus aut veritatis dolorum delectus quasi corporis animi quas?
              </div>
            </div>
          </div>
        </div>
        <div class="mb-28"></div>
        <div id="CreateComment" v-if="true"
          class=" absolute flex items-center justify-between bottom-0 bg-white h-[85px] lg:max-w-[550px] w-full py-5 px-8 border-t-2">
          <div :class="inputFocused?'border-2 border-gray-400':'border-2 border-[#f1f1f2]'"
            class=" bg-[#f1f1f2] flex items-center rounded-lg w-full lg:max-w-[420px]">
            <input v-model="comment" @focus="$event=>inputFocused=true" @blur="inputFocused=false"
              class="bg-[#f1f1f2] text-[14px] focus:outline-none w-full lg:max-w-[420px] p-2 rounded-lg" type="text"
              placeholder="Add comment...">
          </div>
          <button :disabled="!comment" @click="$event=>addComment()"
            :class="comment?'text-[#f02c56] cursor-pointer':'text-gray-400'"
            class=" font-semibold text-sm ml-5 pr-1">Post</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const route = useRoute()
const router = useRouter()

let video = ref(null)
let isLoaded = ref(false)
let comment = ref(null)
let inputFocused = ref(false)
watch(() => isLoaded.value, () => {
  if (isLoaded.value) {
    setTimeout(() => {
      video.value.play()
    }, 500);
  }
})
onMounted(() => {
  isLoaded.value = true
  video.value.play()
  // video.value.addEventListener('loadeddata', (e) => {
  //   console.log(22, e);
  //   if (e.target) {
  //     console.log(33, e.target);
  //     setTimeout(() => {
  //       isLoaded.value = true
  //     }, 300);
  //   }
  // })
})
onBeforeUnmount(() => {
  video.value.pause()
  video.value.currentTime = 0
  video.value.src = ''
})
</script>
