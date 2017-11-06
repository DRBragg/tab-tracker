<template>
  <v-layout>
    <v-flex xs4>
      <panel title="Add Song">
        <v-text-field
          required
          :rules="[required]"
          label="Title"
          v-model="song.title"
        ></v-text-field>

        <v-text-field
          required
          :rules="[required]"
          label="Artist"
          v-model="song.artist"
        ></v-text-field>

        <v-text-field
          required
          :rules="[required]"
          label="Genre"
          v-model="song.genre"
        ></v-text-field>

        <v-text-field
          required
          :rules="[required]"
          label="Album"
          v-model="song.album"
        ></v-text-field>

        <v-text-field
          required
          :rules="[required]"
          label="Album Image URL"
          v-model="song.albumImage"
        ></v-text-field>

        <v-text-field
          required
          :rules="[required]"
          label="Youtube Id"
          v-model="song.youtubeId"
        ></v-text-field>
      </panel>
    </v-flex>
    <v-flex xs8>
      <panel title="Song Data" class="ml-4">
        <v-text-field
          required
          :rules="[required]"
          label="Tab"
          v-model="song.tab"
          multi-line
        ></v-text-field>

        <v-text-field
          required
          :rules="[required]"
          label="Lyrics"
          v-model="song.lyrics"
          multi-line
        ></v-text-field>
      </panel>
      <div class="danger-alert" v-if="error">
        {{error}}
      </div>
      <v-btn dark class="cyan ml-4" @click="createSong">Create Song</v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
import Panel from '@/components/Panel'
import SongsService from '@/services/SongsService'

export default {
  data () {
    return {
      song: {
        title: null,
        artist: null,
        genre: null,
        album: null,
        albumImage: null,
        youtubeId: null,
        lyrics: null,
        tab: null
      },
      error: null,
      required: (value) => !!value || 'Required.'
    }
  },
  methods: {
    async createSong () {
      this.error = null
      const areAllFieldsFilledIn = Object
        .keys(this.song)
        .every(key => !!this.song[key])

      if (!areAllFieldsFilledIn) {
        this.error = 'Please fill in all the required fields'
        return
      }

      try {
        await SongsService.post(this.song)
        this.$router.push({
          name: 'songs'
        })
      } catch (err) {
        console.log(err)
      }
    }
  },
  components: {
    Panel
  }
}
</script>


<style scoped>

</style>
