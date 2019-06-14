<template>
  <v-container fluid pa-0 grid-list-md>
    <v-container class="feed">
      <v-layout pa-2 mb-2 column wrap>
        <v-flex v-for="(msg, i) in feed" :key="i">
          <div v-if="msg.id == 0" class="speech-bubble-right">{{ msg.content }}</div>
          <div v-else class="speech-bubble-left">{{ msg.content }}</div>
        </v-flex>
      </v-layout>
    </v-container>
    <v-container fluid pa-1 class="send" overflow-hidden>
      <v-layout align-end justify-center row fill-height>
        <v-textarea
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
        ></v-textarea>
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
  max-width: 80%;
  float: right;
  padding: 2px 10%;
  margin-bottom: 1em;
  position: relative;
  background: white;
  border-radius: 0.4em;
}

.speech-bubble-right:after {
  content: "";
  position: absolute;
  right: 0;
  top: 60%;
  width: 0;
  height: 0;
  border: 0.969em solid transparent;
  border-left-color: white;
  border-right: 0;
  border-bottom: 0;
  margin-top: -0.484em;
  margin-right: -0.969em;
}

.speech-bubble-left {
  max-width: 80%;
  float: left;
  padding: 2px 10%;
  position: relative;
  background: lime;
  border-radius: 0.4em;
}

.speech-bubble-left:after {
  content: "";
  position: absolute;
  left: 0;
  top: 60%;
  width: 0;
  height: 0;
  border: 0.969em solid transparent;
  border-right-color: lime;
  border-left: 0;
  border-bottom: 0;
  margin-top: -0.484em;
  margin-left: -0.969em;
}
</style>


<script>
export default {
  name: "Chat",
  data: function() {
    return {
      content: "",
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
            "At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum necessitatibus saepe eveniet ut et voluptates repudiandae sint et molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis doloribus asperiores repellat."
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
      }
    }
  }
};
</script>

