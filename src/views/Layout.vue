<template>
  <div>
    <v-card class="overflow-hidden">
      <v-app-bar
        absolute
        color="#fcb69f"
        dark
        shrink-on-scroll
        src="https://picsum.photos/1920/1080?random"
        scroll-target="#scrolling-techniques-2"
      >
        <template v-slot:img="{ props }">
          <v-img v-bind="props" gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"></v-img>
        </template>

        <v-app-bar-nav-icon></v-app-bar-nav-icon>

        <v-toolbar-title>Cloud Music</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>
      <v-sheet id="scrolling-techniques-2" class="overflow-y-auto" max-height="600">
        <v-container style="height: 1px;"></v-container>
      </v-sheet>
    </v-card>
    <v-container class="box">
      <v-row>
        <v-col cols="3">
          <v-container>
            <v-card min-height="600" class="overflow-hidden">
              <v-navigation-drawer v-model="drawer" :expand-on-hover="expandOnHover" :mini-variant="miniVariant" :right="right" absolute>
                <v-list dense nav class="py-0">
                  <v-list-item two-line :class="miniVariant && 'px-0'">
                    <v-list-item-avatar>
                      <img
                        @click="miniVariant = !miniVariant"
                        src="data:image/jpeg;base64,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"
                      />
                    </v-list-item-avatar>

                    <v-list-item-content>
                      <v-list-item-title><h3 class="gutter">Cloud Music</h3> </v-list-item-title>
                      <v-list-item-subtitle class="gutter">Super Admin</v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>

                  <v-divider></v-divider>

                  <v-list-item v-for="item in items" :key="item.title" link>
                    <template v-if="item.subMenus.length === 0">
                      <v-list-item-icon>
                        <v-icon>{{ item.icon }}</v-icon>
                      </v-list-item-icon>

                      <v-list-item-content>
                        <router-link :to="item.url">
                          <v-list-item-title class="gutter">{{ item.title }}</v-list-item-title>
                        </router-link>
                      </v-list-item-content>
                    </template>
                    <template v-else>
                      <v-list-group value="true" style="margin-left:-10px;">
                        <template v-slot:activator>
                          <v-list-item-icon>
                            <v-icon>{{ item.icon }}</v-icon>
                          </v-list-item-icon>
                          <v-list-item-title>{{ item.title }}</v-list-item-title>
                        </template>
                        <v-list-item-content style="margin-left:20px;">
                          <v-list-item v-for="(menu, i) in item.subMenus" :key="i" link>
                            <v-list-item-icon class="gutter">
                              <v-icon :v-text="menu.icon">{{ menu.icon }}</v-icon>
                            </v-list-item-icon>
                            <router-link :to="menu.url">
                              <v-list-item-title :v-text="menu.title" class="gutter">{{ menu.title }}</v-list-item-title>
                            </router-link>
                          </v-list-item>
                        </v-list-item-content>
                      </v-list-group>
                    </template>
                  </v-list-item>
                </v-list>
              </v-navigation-drawer>
            </v-card>
          </v-container>
        </v-col>
        <v-col cols="9">
          <router-view />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Layout',
  data() {
    return {
      user: this.$store.state.user,
      drawer: true,
      items: this.$store.state.menuList1,
      colors: ['primary', 'blue', 'success', 'red', 'teal'],
      right: true,
      miniVariant: false,
      expandOnHover: false,
      background: true
    }
  },
  components: {},
  created() {},
  mounted() {},
  methods: {
    logout() {
      alert('logout')
      localStorage.removeItem('token')
      this.$store.commit('setUser', null)
      this.$router.push('/login')
    }
  },
  computed: {}
}
</script>

<style scoped lang="scss">
.box {
  margin-top: 90px;
  a {
    color: rgb(14, 9, 9);
    text-decoration: none;
  }
}
</style>
