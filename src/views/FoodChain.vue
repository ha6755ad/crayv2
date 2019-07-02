<template>
  <div>
    <v-container grid-list-xl fluid>
      <v-layout wrap align-start justify-center>
        <v-flex xs12 sm6 offset-sm3 d-flex>
          <v-card>
            <v-toolbar color="orange" dark>
              <v-toolbar-side-icon></v-toolbar-side-icon>

              <v-toolbar-title class="text-xs-center">{{
                foodchain.title
              }}</v-toolbar-title>

              <v-spacer></v-spacer>

              <v-btn icon>
                <v-icon>search</v-icon>
              </v-btn>
            </v-toolbar>

            <v-list subheader>
              <v-subheader>Recent chat</v-subheader>
              <v-list-tile
                v-for="item in items"
                :key="item.title"
                avatar
                @click=""
              >
                <v-list-tile-avatar>
                  <img :src="item.avatar" />
                </v-list-tile-avatar>

                <v-list-tile-content>
                  <v-list-tile-title v-html="item.title"></v-list-tile-title>
                </v-list-tile-content>

                <v-list-tile-action>
                  <v-icon :color="item.active ? 'teal' : 'grey'"
                    >chat_bubble</v-icon
                  >
                </v-list-tile-action>
              </v-list-tile>
            </v-list>

            <v-divider></v-divider>

            <v-list subheader>
              <v-subheader>Previous chats</v-subheader>

              <v-list-tile
                v-for="item in items2"
                :key="item.title"
                avatar
                @click=""
              >
                <v-list-tile-avatar>
                  <img :src="item.avatar" />
                </v-list-tile-avatar>

                <v-list-tile-content>
                  <v-list-tile-title v-html="item.title"></v-list-tile-title>
                </v-list-tile-content>
              </v-list-tile>
            </v-list>
          </v-card>
        </v-flex>
            <v-flex d-flex order-md-5>
              <v-card color="orange">
                <google-map
                  class="gmap"
                  name="example"
                  v-for="block in blocks"  
                  :key="block.id"        
                  :block="block"
                >
                </google-map>
              </v-card>
            </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import GoogleMap from "@/components/GoogleMap.vue";
import Gmap from "@/service/Gmap.js";

export default {
  components: {
    GoogleMap
  },
  data() {
    return {
      blocks: [],
      foodchain: {
        title: "Lehi Tech FoodChain"
      }
    };
  },
  created() {
    Gmap.getGroups()
      .then(response => {
        this.blocks = response.data; // <--- set the groups data
        alert(this.blocks[0].id)
      })
      .catch(error => {
        // eslint-disable-next-line no-console
        console.log("Hey look at this error:", error.response);
      });
  }
};
</script>
<style scoped></style>
