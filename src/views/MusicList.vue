<template>
  <v-card max-width="600" class="mx-auto">
    <v-responsive class="overflow-y-auto" max-height="400">
      <div class="pa-6 text-center">
        Scroll down
      </div>

      <v-responsive height="200vh" class="text-center pa-2">
        <v-responsive min-height="50vh"></v-responsive>
        <div class="text-center body-2 mb-12">The card will appear below:</div>

        <v-lazy
          v-model="isActive"
          :options="{
            threshold: 0.5
          }"
          min-height="200"
          transition="fade-transition"
        >
          <v-card class="mx-auto" max-width="336">
            <v-card-title>Card title</v-card-title>

            <v-card-text>
              Phasellus magna. Quisque rutrum. Nunc egestas, augue at pellentesque laoreet, felis eros vehicula leo, at malesuada velit leo
              quis pede. Aliquam lobortis. Quisque libero metus, condimentum nec, tempor a, commodo mollis, magna. In turpis. In dui magna,
              posuere eget, vestibulum et, tempor auctor, justo. In turpis. Pellentesque dapibus hendrerit tortor. Ut varius tincidunt
              libero.
            </v-card-text>
          </v-card>
        </v-lazy>
      </v-responsive>
    </v-responsive>
    <v-toolbar color="light-blue" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>My music</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-view-module</v-icon>
      </v-btn>
    </v-toolbar>

    <v-list two-line subheader>
      <v-subheader inset>Folders</v-subheader>

      <v-list-item v-for="item in items" :key="item.title">
        <v-list-item-avatar>
          <v-icon :class="[item.iconClass]" v-text="item.icon"></v-icon>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title v-text="item.title"></v-list-item-title>
          <v-list-item-subtitle v-text="item.subtitle"></v-list-item-subtitle>
        </v-list-item-content>

        <v-list-item-action>
          <v-btn icon>
            <v-icon color="grey lighten-1">mdi-information</v-icon>
          </v-btn>
        </v-list-item-action>
      </v-list-item>

      <v-divider inset></v-divider>

      <v-subheader inset>Files</v-subheader>

      <v-list-item v-for="item in items2" :key="item.title">
        <v-list-item-avatar>
          <v-icon :class="[item.iconClass]" v-text="item.icon"></v-icon>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title v-text="item.title"></v-list-item-title>
          <v-list-item-subtitle v-text="item.subtitle"></v-list-item-subtitle>
        </v-list-item-content>

        <v-list-item-action>
          <v-btn icon>
            <v-icon color="grey lighten-1">mdi-information</v-icon>
          </v-btn>
        </v-list-item-action>
      </v-list-item>
    </v-list>
  </v-card>
</template>

<script>
export default {
  name: 'MusicList',
  data: () => ({
    items: [
      { icon: 'folder', iconClass: 'grey lighten-1 white--text', title: 'Photos', subtitle: 'Jan 9, 2014' },
      { icon: 'folder', iconClass: 'grey lighten-1 white--text', title: 'Recipes', subtitle: 'Jan 17, 2014' },
      { icon: 'folder', iconClass: 'grey lighten-1 white--text', title: 'Work', subtitle: 'Jan 28, 2014' }
    ],
    items2: [
      { icon: 'assignment', iconClass: 'blue white--text', title: 'Vacation itinerary', subtitle: 'Jan 20, 2014' },
      { icon: 'call_to_action', iconClass: 'amber white--text', title: 'Kitchen remodel', subtitle: 'Jan 10, 2014' }
    ]
  })
}
</script>

<style scoped lang="scss"></style>
