<template>

<MyContainer>
<ChatWindow>
<ChatMessage  v-bind:username="username" v-bind:time="time">
  {{message}}
</ChatMessage>
</ChatWindow>
</MyContainer>

</template>

<script>

import MyContainer from "./components/MyContainer.vue";
import ChatMessage from "./components/ChatMessage.vue";
import ChatWindow from "./components/ChatWindow.vue";

export default {
  name: "App",
  components: {
    MyContainer,
    ChatMessage,
    ChatWindow
  },
  data(){
  return {
    time: [],
    username: [],
    message: []
  }
  },
  methods: {
    Get_Mes(){
      this.axios.get('https://61bcd385d8542f0017824a2a.mockapi.io/messages')
        .then((response) => {
          console.log(response.data)
          for (let i = 0; i < 71; i++) {
            this.time[i] = response.data[i]['datetime']
            this.username[i] = response.data[i]['author']
            this.message[i] = response.data[i]['text']
          }
        })
    }
  },
  mounted() {
    this.Get_Mes();
  }
};

</script>

<style>

body {
  margin: 0;
  background-color: #f9f9fa;
}

</style>