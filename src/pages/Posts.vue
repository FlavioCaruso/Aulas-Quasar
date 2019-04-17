<template>
  <q-page class="container">
    <div class="row justify-center q-pa-lg">
      <div class="col-xs-12 col-md-4 col-lg-3 q-mx-md q-my-md" v-for="(post, index) in posts" :key="index">
        <q-card>
          <q-card-media>
            <img :src="post.better_featured_image.source_url">
          </q-card-media>
          <q-card-title v-html="post.title.rendered" style="height:130px">
          </q-card-title>
          <q-card-separator />
          <q-card-actions>
            <q-btn push color="primary" label="Detalhes" class="full-width" @click="detalhar(post.id)" />
          </q-card-actions>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import { mapActions, mapState, mapMutations } from 'vuex'
export default {
  name: 'Posts',
  mounted () {
    this.CLEAR_ARTIGO()
    this.setPosts()
  },
  computed: {
    ...mapState('posts', ['posts'])
  },
  methods: {
    ...mapActions('posts', ['setPosts']),
    ...mapMutations('posts', ['CLEAR_ARTIGO']),
    detalhar (id) {
      this.$router.push(`artigo/${id}`)
    }
  }
}
</script>
<style>
</style>
