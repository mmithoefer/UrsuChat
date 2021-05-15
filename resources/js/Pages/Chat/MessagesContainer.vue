<template>
  <div class="w-full">
    <div class="h-96 p-2 flex flex-col-reverse overflow-scroll">
      <div v-for="(message, index) in messages" :key="index">
        <MessageItem :message="message"/>
      </div>
    </div>
  </div>
</template>

<script>
import MessageItem from "./MessageItem";

export default {
  components: {MessageItem},
  props: ['messages']
}
</script>