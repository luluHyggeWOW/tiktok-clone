<template>
  <div id="EditProfileOverlay"
    class=" fixed flex justify-center pt-14 md:pt-[105px] z-50 top-0 left-0 w-full h-full bg-black bg-opacity-50 overflow-auto">
    <div class=" relative bg-white w-full max-w-[700px] sm:h-[580px] h-[655px] mx-3 p-4 rounded-lg mb-10"
      :class="!uploadedImage?'h-[655px]':'h-[580px]'">
      <div class=" absolute flex items-center justify-between w-full p-5 left-0 top-0 border-b border-gray-300">
        <div class=" text-[22px] font-medium">Edit profile</div>
        <button @click="$event=>$generalStore.isEditProfileOpen=false">
          <Icon name="mdi:close" size="25"></Icon>
        </button>
      </div>
      <div class="h-[calc(500px-200px)]" :class="!uploadedImage?'mt-16':'mt-[58px]'">
        <div v-if="!uploadedImage">
          <div id="ProfilePhotoSection" class="flex flex-col border-b sm:h-[118px] h-[145px] px-1.5 py-2 w-full">
            <div class=" font-semibold text-[15px] sm:mb-0 mb-1 text-gray-700 sm:w-[160px] sm:text-left text-center">
              Profile photo
            </div>
            <div class="flex items-center justify-center sm:mt-6">
              <label for="image" class=" relative cursor-pointer">
                <img class=" rounded-full" width="95" src="https://picsum.photos/id/8/300/320" alt="">
                <div
                  class=" absolute bottom-0 right-0 rounded-full bg-white shadow-xl border-gray-300 inline-block w-[32px]">
                  <Icon name="ph:pencil-simple-line-bold" size="17" class="-mt-1 ml-0.5"></Icon>
                </div>
              </label>
              <input class="hidden" type="file" id="image" @input="getUploadedImage"
                accept="imag/png,image/jpeg,image/jpg">
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
const { $userStore, $generalStore } = useNuxtApp();
let uploadedImage = ref(null)
</script>

