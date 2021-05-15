<template>
  <hr class="mb-2">
  <div class="relative h-10 m-1">
    <div class="grid grid-cols-6">
      <input
          type="text"
          v-model="message"
          @keyup.enter="sendMessage()"
          placeholder="Sage was du möchtest..."
          class="col-span-5 outline-none p-1 rounded-lg px-3 mx-2"
      />
      <button
          @click="sendMessage()"
          class="place-self-end bg-gray-500 hover:bg-blue-700 p-1 mt-1 mx-2 rounded text-white"
      >
        Send
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['room'],
  data: function () {
    return {
      message: ''
    }
  },
  methods: {
    sendMessage() {
      if (this.message == '') {
        return;
      }

      axios.post('chat/room/' + this.room.id + '/message', {
        message: this.message
      })
          .then(response => {
            if (response.status == 201) {
              this.message = '';
              this.$emit('MessageSent');
            }
          })
          .catch(error => {
            console.log(error);
          })
    }
  }
}
</script>