<template>
  <v-app id="keep">
    <v-app-bar
      app
      dark
      clipped-left
      color="indigo accent-2"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"/>
      <span class="title ml-3 mr-5">Beloved&nbsp;<span class="font-weight-light">Music</span></span>
      <v-text-field
        solo-inverted
        flat
        hide-details
        label="Search"
        prepend-inner-icon="mdi-magnify"
      />
      <v-spacer/>
      <v-btn icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <v-btn
        icon
        large
      >
        <v-avatar
          size="32px"
          item
        >
          <v-img
            src="http://q1.qlogo.cn/g?b=qq&nk=1762479428&s=100"
            alt="Vuetify"
          />
        </v-avatar>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
      color="grey lighten-4"
    >
      <v-list
        dense
        class="grey lighten-4"
      >
        <template v-for="(item, i) in items">
          <v-row
            v-if="item.heading"
            :key="i"
            align="center"
          >
            <v-col cols="6">
              <v-subheader v-if="item.heading">
                {{ item.heading }}
              </v-subheader>
            </v-col>
            <v-col
              cols="6"
              class="text-right"
            >
              <v-btn
                small
                text
              >edit
              </v-btn>
            </v-col>
          </v-row>
          <v-divider
            v-else-if="item.divider"
            :key="i"
            dark
            class="my-4"
          />
          <v-list-item
            v-else
            :key="i"
            link
          >
            <v-list-item-action>
              <v-icon>{{item.icon}}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="grey--text">
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <v-container
        fluid
        class="grey lighten-4 fill-height"
      >
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  props: {
    source: String
  },
  data: () => ({
    drawer: null,
    items: [
      {
        icon: 'mdi-bookmark-music',
        text: '每日推荐'
      },
      { divider: true },
      { heading: '推荐' },
      {
        icon: 'mdi-playlist-music',
        text: '推荐歌单'
      },
      { divider: true },
      {
        icon: 'mdi-equalizer',
        text: '排行榜'
      },
      {
        icon: 'mdi-radio',
        text: '主播电台'
      },
      {
        icon: 'mdi-movie-filter',
        text: 'MV'
      },
      {
        icon: 'mdi-account-music',
        text: '歌手'
      },
      {
        icon: 'mdi-order-bool-ascending',
        text: '分类'
      },
      { divider: true },
      {
        icon: 'mdi-account',
        text: '个人中心'
      },
      {
        icon: 'mdi-cog',
        text: '设置'
      }
    ]
  })
}
</script>

<style>
  #keep .v-navigation-drawer__border {
    display: none
  }
</style>
