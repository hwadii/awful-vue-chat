<template>
  <v-container fluid pa-0 grid-list-xl overflow-x-hidden>
    <!-- <v-toolbar>
      <v-spacer></v-spacer>
      <v-toolbar-title>Chat</v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar> -->
    <v-container>
      <v-layout pa-3 align-center justify-start fill-height column>
        <v-flex xs12>
          <v-card dark color="primary">
            <v-card-text>Hello</v-card-text>
          </v-card>
        </v-flex>
        <v-flex xs2>
          <v-card dark color="secondary">
            <v-card-text>Hi</v-card-text>
          </v-card>
        </v-flex>
        <v-flex xs2>
          <v-card dark color="primary">
            <v-card-text>Hello</v-card-text>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
    <v-container fluid class="send">
      <v-layout align-end justify-center row fill-height>
        <v-textarea
          @click:append="sayHi()"
          rows="1"
          hide-details
          solo
          append-icon="send"
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
</style>


<script>
export default {
  name: "Chat",
  data: function() {
    return {
      m: 2
    };
  },
  methods: {
    sayHi: () => {
      return "hi";
    }
  }
};
</script>

