<template>
  <v-layout>
    <v-flex xs6>
      <panel title="Song Data">
        <v-layout>
          <v-flex xs6>
            <div class="song-title">
              {{song.title}}
            </div>
            <div class="song-artist">
              {{song.artist}}
            </div>
            <div class="song-genre">
              {{song.genre}}
            </div>
          </v-flex>

          <v-flex xs6>
            <img class="album-image" :src="song.albumImage" />
            <br />
            {{song.album}}
          </v-flex>
        </v-layout>
      </panel>
    </v-flex>

    <v-flex xs6 class="ml-4">
      <panel title="Tabs">
        <textarea
          readonly
          v-model="song.tab">
        </textarea>
      </panel>
    </v-flex>
  </v-layout>
</template>

<script>
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'

export default {
  data () {
    return {
      song: {}
    }
  },
  components: {
    Panel
  },
  async mounted () {
    const songId = this.$store.state.route.params.songId
    this.song = (await SongsService.show(songId)).data
  }
}
</script>


<style scoped>
.song-title {
  font-size: 30px;
}
.song-artist {
  font-size: 24px;
}
.song-genre {
  font-size: 18px;
}
.album-image {
  width: 70%;
  margin: 0 auto;
}
textarea {
  width: 100%;
  font-family: monospace;
  border: none;
  height: 600px;
  padding: 20px;
  overflow: auto;
}
</style>
