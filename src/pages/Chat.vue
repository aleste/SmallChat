<template>
  <q-page class="flex column">
    <q-banner inline-actions class="bg-grey-4">
      User is offline.
    </q-banner>
    <div class="q-pa-md column col justify-end">
      <q-chat-message
        v-for="(message, index) in messages"
        :name="message.from"
        :text="[message.text]"
        :key="index"
        :sent="message.from === 'me' ? true : false"
      />
    </div>
    <q-footer elevated>
      <q-toolbar>
        <q-form class="full-width">
          <q-input
            bg-color="white"
            class="q-pa-md full-width"
            rounded
            outlined
            bottom-slots
            v-model="newMessage"
            label="Send a message"
            maxlength="12"
            dense
          >
            <template v-slot:after>
              <q-btn
                color="white"
                round
                dense
                flat
                icon="send"
                @click="sendMessage"
              />
            </template>
          </q-input>
        </q-form>
      </q-toolbar>
    </q-footer>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      newMessage: '',
      messages: [
        {
          text: 'Hola como andas?',
          from: 'me',
        },
        {
          text: 'viento y bosque',
          from: 'Other',
        },
      ],
    }
  },
  methods: {
    sendMessage() {
      console.log('entr')
      this.messages.push({
        text: this.newMessage,
        from: 'me',
      })
    },
  },
}
</script>
