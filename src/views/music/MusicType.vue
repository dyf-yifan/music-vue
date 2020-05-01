<template>
  <div>
    <h3>歌曲类型管理</h3>
    <div v-for="(type, index) in types" :key="index">
      {{ type.songListName }}
    </div>
    <v-card class="mx-auto" max-width="400">
      <v-img class="white--text align-end" height="200px" src="https://cdn.vuetifyjs.com/images/cards/docks.jpg">
        <v-card-title>Top 10 Australian beaches</v-card-title>
      </v-img>

      <v-card-subtitle class="pb-0">Number 10</v-card-subtitle>

      <v-card-text class="text--primary">
        <div>Whitehaven Beach</div>

        <div>Whitsunday Island, Whitsunday Islands</div>
      </v-card-text>

      <v-card-actions>
        <v-btn color="orange" text>
          Share
        </v-btn>

        <v-btn color="orange" text>
          Explore
        </v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'MusicType',
  data() {
    return {
      types: [],
      typeChildSongList: []
    }
  },
  created() {
    this.getSongListType()
  },
  methods: {
    getSongListType() {
      let roleId = localStorage.roleId
      console.log(roleId)
      console.log(localStorage)
      console.log(localStorage.getItem)
      console.log(localStorage.getItem('roleId'))

      this.axios({
        method: 'get',
        url: 'http://localhost:8080/songList/type?roleId=' + roleId,
        headers: {
          'Content-Type': 'application/x-www-form-urlencoded'
        }
      }).then((res) => {
        //获取各种类型及属于该类型的歌单数据
        this.types = res.data.data
        console.log(this.types)
        //取出第一种类型的所有歌单，作为默认tab页上显示的数据
        this.typeChildSongList = this.types[0].child
        console.log(this.typeChildSongList)
      })
    }
  }
}
</script>

<style scoped lang="scss"></style>
