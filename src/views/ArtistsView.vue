<script>
import spotifyAPI from "../utils/spotifyAPI";
import ArtistAlbumComponent from "../components/ArtistAlbumComponent.vue";

export default {
  name: "MainView",
  components: {
    ArtistAlbumComponent,
  },
  methods: {
    a() {
      return "";
    },
  },
  data() {
    return {
      albums: [],
    };
  },
  async created() {
    //TODO: pass album id
    const id = this.$route.params.id;
    const artistAlbums = await spotifyAPI.getArtistAlbums(id);
    this.albums = artistAlbums.items;
    console.log(this.albums[1]);
  },
};
</script>

<template>
  <div class="main">
    <div
      class="albums-container"
      v-for="(artistaAlbum, index) in albums"
      :key="index"
    >
      <ArtistAlbumComponent
        :name="artistaAlbum.name"
        :tracks="artistaAlbum.tracks"
        :img="artistaAlbum.img"
        :date="artistaAlbum.date"
      ></ArtistAlbumComponent>
    </div>
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {
  .main {
    display: flex;
    max-height: 70vh;
    max-width: 70vh;
  }

  .albums-container {
    text-align: center;
    overflow-y: auto;
    vertical-align: middle;
    display: grid;
    grid-template-columns: auto auto;
    grid-gap: 10px;
    padding: 10px;
  }
}
</style>
