<template>
  <div class="bg-gray-100 m-2 rounded p-2 shadow-md">
    <span class="text-blue-600">{{ message.user.name }}: </span>
    <span class="text-gray-800">{{ message.message }}</span>
  </div>
</template>

<script>
export default {
  props: ['message']
}
</script>