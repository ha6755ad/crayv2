<template>
  <div>
      <v-container fluid style="max-width:75%">
        <v-layout>
          <v-flex>
            <v-card>
              <v-toolbar color="white" light>
                <v-toolbar-side-icon @click.stop="drawer = !drawer">
                </v-toolbar-side-icon>

                <v-toolbar-title class="text-xs-center"></v-toolbar-title>

                <v-spacer></v-spacer>
                <v-container hidden-xs-only row align-center justify-end fill-height xs12 >
                  <v-btn flat fab>
                      <v-icon>dashboard</v-icon>
                  </v-btn> 
                  <v-btn flat fab>
                      <v-icon>perm_identity</v-icon>
                  </v-btn> 
                  <v-btn flat fab>
                      <v-icon>account_balance_wallet</v-icon>
                  </v-btn> 
                  <v-btn flat fab>
                      <v-icon>ballot</v-icon>
                  </v-btn> 
                </v-container>

              </v-toolbar>

              <v-card height=100%>
                  <v-card-title>Title</v-card-title>
                  <workspace :apps="apps"></workspace>
              </v-card> 

            <v-navigation-drawer v-model="drawer" temporary absolute>
              <v-list>
                <v-list-tile>
                  <v-list-tile-title class="title">Hut</v-list-tile-title>
                </v-list-tile>
              </v-list>

              <v-divider></v-divider>

              <v-list dense class="pt-0">
                <v-list-tile v-for="item in items" :key="item.title">
                  <v-list-tile-action>
                    <v-icon>{{ item.icon }}</v-icon>
                  </v-list-tile-action>

                  <v-list-tile-content>
                    <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                  </v-list-tile-content>
                </v-list-tile>
              </v-list>
            </v-navigation-drawer>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </div>
 
</template>

<script>
export default {
  name: "ProductMain",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
