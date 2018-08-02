<template>
  <v-app>
    <v-navigation-drawer
      class="navigation-drawer"
      :clipped="false"
      v-model="drawer"
      fixed
      app
    >
      <v-toolbar dark class="navigation-drawer-toolbar">
        <v-list class="pa-0 pl-3">
          <v-list-tile avatar>
            <v-list-tile-action>
              <img height="60px" src="https://pbs.twimg.com/profile_images/948646512124346368/JM7YCz_n_400x400.jpg">
            </v-list-tile-action>
            <v-list-tile-title class="headline">
              <span class="font-weight-black font-italic">PVP</span>
              <span class=".font-weight-thin font-italic">LIVE</span>
            </v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-toolbar>

      <v-divider></v-divider>
  
      <v-list class="">
        <v-list-tile
          value="true"
          v-for="(item, i) in items"
          :key="i"
          v-model="activeTile"
          @click="activeTile = item.title"
          ripple
          active-class="default-class active-tile"
        >
          <v-list-tile-action class="pl-3">
            <v-icon v-if="activeTile === item.title" v-html="item.action"></v-icon>
            <v-icon v-else color="deep-purple lighten-4" v-html="item.action"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title class="list-title" v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>

    <v-toolbar class="pt-0 pb-0 main-toolbar" app color="white" height="64">
      <v-container fluid class="pa-0" fill-height>
        <v-layout row wrap align-center justify-space-between>
          <v-flex hidden-md-and-down lg2>
            <v-btn class="ma-0 ml-2" icon @click.stop="drawer = !drawer">
              <v-icon x-large v-html="!drawer ? 'arrow_right' : 'arrow_left'"></v-icon>
            </v-btn>
          </v-flex>
          <v-flex xs2 hidden-lg-and-up lg2 md2>
            <v-btn class="ma-0 ml-3" icon @click.stop="drawer = !drawer">
              <v-icon x-large>menu</v-icon>
            </v-btn>
          </v-flex>
          <v-flex lg10 md10 xs10 fill-height>
            <v-container fluid class="pa-0" fill-height>
              <v-layout row wrap fill-height justify-end>
                <v-flex hidden-xs-only lg2 md3 sm4 fill-height>
                  <v-card ripple dark tile flat color="green accent-3" height="100%" class="text-xs-center">
                    <v-layout row warp align-center justify-center fill-height>
                      <v-flex xs12>
                        <v-container class="pa-0">
                          <v-icon>add_circle</v-icon>
                          <span class="title font-weight-bold">Add Funds</span>
                        </v-container>
                      </v-flex>
                    </v-layout>
                  </v-card>
                </v-flex>
                <v-flex lg2 md3 sm4 xs5 fill-height>
                  <v-card ripple tile flat color="white" height="100%" class="text-xs-center">
                    <v-layout align-center justify-center column fill-height>
                      <v-flex d-flex xs12 align-end>
                        <span class="title font-weight-bold">{{ balance | dollars }}</span>
                      </v-flex>
                      <v-flex d-flex xs12 align-start>
                        <span class="black--text">BALANCE</span>
                      </v-flex>
                    </v-layout>
                  </v-card>
                </v-flex>
              </v-layout>
            </v-container>
          </v-flex>
        </v-layout>
      </v-container>

      <v-card ripple tile flat height="100%" class="pa-0 avatar-card">
        <v-avatar
          :tile="true"
          size="100%"
          color="grey lighten-4"
        >
          <img src="https://store.playstation.com/store/api/chihiro/00_09_000/container/US/en/999/UP0102-NPUP10015_00-AVAVJJOEFACE0000/1520452405000/image?w=240&h=240&bg_color=000000&opacity=100&_version=00_09_000" alt="avatar">
        </v-avatar>
      </v-card>
    </v-toolbar>
    <v-content>
      <router-view/>
    </v-content>
  </v-app>
</template>

<script>
export default {
  filters: {
    dollars: num => `$${parseFloat(num).toFixed(2)}`
  },
  data () {
    return {
      drawer: true,
      balance: 0.00,
      activeTile: 'Games',
      items: [{
        action: 'dashboard',
        title: 'Dashboard'
      }, {
        action: 'games',
        title: 'Games'
      }, {
        action: 'person',
        title: 'Leaderboards'
      }, {
        action: 'contact_support',
        title: 'Support'
      }]
    }
  }
}
</script>

<style lang="scss">
  .navigation-drawer {
    background-color: #1c1f2a !important;

    .navigation-drawer-toolbar {
      background-color: #222633 !important;
      overflow: hidden;
    }

    .list-title {
      color: #D1C4E9 !important;
    }
  }
  .main-toolbar {
    .v-toolbar__content {
      padding-right: 0px !important;
      padding-left: 0px !important;
    }
    .avatar-card {
      max-width:80px;
    }
  }
  .active-tile {
    color: #685bc7 !important;
  }
</style>