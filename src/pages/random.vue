<template>
  <div class="take-up-the-full-page">
    <div class="column justify-center content-center items-center" style="height:100%;width:100%;">
      <div id="front-and-center-yo col-3" v-if="src!==''">
        <iframe :src="src" frameBorder="0" class="giphy-embed iframe-size" allowFullScreen></iframe><p><a :href="src"></a></p>
      </div>
      <div class="col-4">
        <q-btn class="button-is-blue" v-on:click="getGif">New Gif!</q-btn>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'gifpage',
  created () {
    this.getGif()
  },
  methods: {
    getGif () {
      this.$axios.get(`https://api.giphy.com/v1/gifs/random?api_key=${this.$store.state.example.giphy_key}`)
        .then(res => {
          this.src = res.data.data.embed_url
        })
    }
  },
  data: function () {
    return {
      src: ''
    }
  }
}
</script>
<style lang="stylus">
@import '~variables'
.take-up-the-full-page
  height calc(100vh - 50px);
  width 100vw
  background: #0F2027;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #2C5364, #203A43, #0F2027);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #2C5364, #203A43, #0F2027); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

#front-and-center-yo
  height:80%;
  width:75%;
  margin auto;
.iframe-size
  width:100%;
.button-is-blue
  background-color:$primary
  color:white
</style>
