<template>
  <q-page>
    <!-- <img alt="Quasar logo" src="~assets/quasar-logo-full.svg"> -->
    <q-spinner v-if="loading" color="primary" size="3em" :thickness="2"/>
    <q-list v-else bordered>
      <q-item clickable v-ripple  v-for="post in posts" :key="post.data.id" @click="showImage(post.data.preview.images[0].source.url)">
        <q-item-section avatar>
          <q-avatar size="90px">
            <img :src="post.data.thumbnail">
          </q-avatar>
        </q-item-section>
        <q-item-section>{{post.data.title}}</q-item-section>
      </q-item>
    </q-list>
    <q-dialog full-width v-model="showImageDialog">
      <q-card>
        <q-card-section class="row items-center">
          <div class="text-h6">Image</div>
          <q-space />
          <q-btn icon="close" flat round dense v-close-popup />
        </q-card-section>
        <q-card-section>
          <q-img
            :src="imageURL"
            spinner-color="green"
          />
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>
<style>
</style>

<script>
export default {
  name: 'PageIndex',
  created () {
    this.$axios.get('https://www.reddit.com/r/aww.json?raw_json=1').then(responseData => {
      console.log(responseData.data.data.children[1].data.thumbnail)
      this.posts = responseData.data.data.children
      this.loading = false
    })
      .catch(error => {
        console.log(error)
      })
  },
  data () {
    return {
      posts: [],
      loading: true,
      showImageDialog: false,
      imageURL: ''
    }
  },
  methods: {
    showImage: function (image) {
      this.imageURL = image
      this.showImageDialog = true
    }
  }
}
</script>
