<template>
  <div>
    <input v-model="inputComputed" :id="`input-${placeholder}`" :placeholder="placeholder" :type="inputType"
      autocomplete="off" :maxlength="max"
      class=" block w-full bg-[#f1f1f2] text-gray-800 border border-gray-300 rounded-md py-2.5 px-3 focus:outline-none">
    <span v-if="error" class="text-red-500 text-[14px] font-semibold">{{error}}</span>
  </div>
</template>

<script setup>
const emit = defineEmits(['update:input'])
const props = defineProps(['input', 'placeholder', 'inputType', 'max', 'autoFocus', 'error'])
const { input, placeholder, inputType, max, autoFocus, error } = toRefs(props)
const inputComputed = computed({
  get: () => input.value,
  set: (val) => emit('update:input', val)
})
// const inputComputed = (val) => {
//   console.log(val);
// }
onMounted(() => {
  if (autoFocus.value) {
    document.getElementById(`input-${placeholder.value}`).focus()
  }
})
</script>

