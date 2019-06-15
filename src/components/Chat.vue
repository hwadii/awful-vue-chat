<template>
  <v-container fluid pa-0 grid-list-md overflow-hidden class="chat-background">
    <v-container class="feed" mb-4>
      <v-layout pa-2 mb-2 column>
        <v-flex v-for="(msg, i) in feed" :key="i">
          <div v-if="msg.id == 0" class="speech-bubble-right">
            <div class="body-2">{{ msg.content }}</div>
          </div>
          <div v-else class="speech-bubble-left">
            <h5 class="font-weight-thin grey--text">{{ msg.name }}</h5>
            <div class="body-2">{{ msg.content }}</div>
          </div>
        </v-flex>
      </v-layout>
    </v-container>
    <v-container pa-1 class="send">
      <v-layout row fill-height>
        <v-text-field
          v-model="content"
          @click:append="sendMessage({id: 0, name: 'Me', content: content})"
          @click:prepend-inner="sendMessage(mock)"
          rows="1"
          hide-details
          solo
          append-icon="send"
          prepend-inner-icon="expand_more"
          auto-grow
          placeholder="Aa"
        ></v-text-field>
      </v-layout>
    </v-container>
  </v-container>
</template>

<style>
.send {
  position: fixed;
  bottom: 0;
}
.speech-bubble-right {
  position: relative;
  text-align: left;
  background: #dcf8c6;
  padding: .5em;
  float: right;
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
  max-width: 30ch;
  word-wrap: break-word;
  border-radius: 0.4em;
}
.speech-bubble-right::after {
  content: "";
  position: absolute;
  right: 0;
  top: 50%;
  width: 0;
  height: 0;
  border: 11px solid transparent;
  border-left-color: #dcf8c6;
  border-right: 0;
  border-bottom: 0;
  box-shadow: 0px 1px rgba(0, 0, 0, 0.1);
  margin-top: -5.5px;
  margin-right: -11px;
}

.speech-bubble-left {
  max-width: 30ch;
  padding: .5em;
  text-align: left;
  float: left;
  position: relative;
  background: white;
  box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
  word-wrap: break-word;
  border-radius: 0.4em;
}
.speech-bubble-left::after {
  content: "";
  position: absolute;
  left: 0;
  top: 50%;
  width: 0;
  height: 0;
  border: 11px solid transparent;
  border-right-color: white;
  border-left: 0;
  border-bottom: 0;
  box-shadow: 0px 1px rgba(0, 0, 0, 0.1);
  margin-top: -5.5px;
  margin-left: -11px;
}
</style>


<script>
export default {
  name: "Chat",
  data: function() {
    return {
      content: "",
      rows: 1,
      mock: {
        id: 1,
        name: "Person",
        content: "Fake message"
      },
      feed: [
        {
          id: 0,
          name: "Me",
          content:
            "At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio."
        },
        {
          id: 1,
          name: "Person",
          content: "Hi"
        },
        {
          id: 0,
          name: "Me",
          content: "Hi"
        }
      ]
    };
  },
  methods: {
    sendMessage: function(msg) {
      if (/^\s*$/.exec(msg.content) == null) {
        this.feed.push({ id: msg.id, name: msg.name, content: msg.content });
        this.content = "";
        this.$vuetify.goTo(9999, "easeOutQuad");
        this.rows = 1;
      }
    }
  }
};
</script>

